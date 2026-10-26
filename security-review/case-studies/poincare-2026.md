# POINCARÉ — From security findings to verifiable code changes

**Independent Solidity security review · Developer remediation · Source-level follow-up**  
**Reviewer:** Mathias Steinbach · **SFS.Labs** (GitHub: [SFS-Labs](https://github.com/SFS-Labs))  
**Client project:** [POINCARÉ](https://github.com/Prakhar-30/POINCARE) by Prakhar Srivastava  
**Original review:** 24 October 2026 · [pinned source 78d75e24](https://github.com/Prakhar-30/POINCARE/commit/78d75e24d7a899fbd488aedd0c0d4de6fe019adb)  
**Follow-up:** 26 October 2026 · [inspected remediation head 7699f626](https://github.com/Prakhar-30/POINCARE/commit/7699f62630404a34fd89298f8994cdc63c9da1ab)

> **Scope disclosure:** This was an independent, scope-limited manual security review by an individual reviewer, **not** a firm audit, certification, formal proof, complete dependency audit, or guarantee of mainnet security. Findings and checks apply only to the revisions and methods stated below.

## Outcome at a glance

| Metric | Verified meaning |
| :-- | :-- |
| **7 Solidity source files** | First-party code in the original, commit-pinned scope (~1,298 LOC) |
| **2 Low findings + 8 Notes** | No Critical, High or Medium issue confirmed **within that review's scope** |
| **222 / 222 Foundry tests** | Original-revision tests independently executed in isolated private CI |
| **Slither / Aderyn / Echidna** | Reports triaged; 3 bounded Echidna assertion properties, 10,001 calls |
| **9 remediation commits / 26 changed files** | Observed in the developer's public remediation branch |
| **240 / 240 tests** | **Maintainer-reported** for remediation; **not independently reproduced by the reviewer** |
| **Second technical assessment** | Read-only follow-up against source changes, tests and residual risks |

POINCARÉ implements a custom-curve Uniswap v4 hook that combines a CUSUM change-point detector, bounded directional spread, optional virtual liquidity depth and LP-share accounting. The engagement began with a five-question threat model supplied by the developer. The independent assessment documented two actionable Low-severity issues and eight observations. The developer then implemented fixes and regression tests. A separate follow-up examined the changes and identified remaining deployment and integration questions.

## Threat model and review boundary

**The client's five questions:** Can intra-block price manipulation distort the detector? Can round-trip swaps drain value? Is initial LP/share accounting vulnerable to inflation? Do read-only quotes match execution? Can kappa or volatility fees escape their configured caps?

**In-scope first-party files:** `PoincareHook.sol`, `PoincareLens.sol`, and the libraries `Cusum.sol`, `DirectionalSignal.sol`, `ControlLaw.sol`, `AsymmetricCurve.sol`, and `PriceLib.sol`. Select OpenZeppelin/Uniswap inherited paths were inspected to understand initialization and settlement, but the dependencies were **not** audited end-to-end.

**Not established:** canonical-router fork execution, deployed-bytecode identity, comprehensive economic/MEV guarantees, arbitrary nonstandard-token compatibility or production readiness. The initial scope did not include independent audit coverage of frontend, SDK or deployment scripts; those were consulted or examined as supporting evidence as appropriate.

## Evidence and methods

- **Manual review:** traced initialization, trading directions, exact-in/exact-out pricing, detector evolution, shadow reserve accounting, liquidity issuance and redemption, config limits and trust boundaries.
- **Foundry:** independently executed the *original* 222-test project suite in isolated private CI; a passing pre-existing test suite is supporting evidence, not a security proof.
- **Slither and Aderyn:** generated and manually triaged scanner output rather than treating every warning as a vulnerability.
- **Echidna:** 10,001 calls on three non-exploit assertion properties covering curve arithmetic and control bounds. These did not exercise full multi-block MEV or production routing.
- **Original off-chain arithmetic model:** 50,000 seeded integer-model cases, separate from EVM execution.
- **Follow-up:** inspected the developer's nine-commit public comparison and remediation regression-test source; independently exercised two sets of 200,000 bounded arithmetic-model checks. These **were not 400,000 Solidity tests**.

## Security findings → developer changes → follow-up

| ID | Original issue | Developer response | Independent follow-up |
| :-- | :-- | :-- | :-- |
| **L-1 / Low** | Unrestricted first PoolKey binding; deploy-and-initialize scripts are non-atomic | Constructor-pinned `expectedPoolId`, wrong-key rejection, bound-pool check, regression source | **Wrong-key binding addressed at source level.** Correct-key initialization by a third party can still preempt the deployer's transaction, including initial price selection; availability/integration caveat remains. |
| **L-2 / Low** | Low raw-unit ratios quantize WAD detector prices, distorting log returns | Internal mid resolution increased to `1e36`, WAD getter/event compatibility preserved, focused tests | **Precision mechanism addressed at source level.** Public `previewDetector()` struct exposes `mid` at a different scale; external callers and a separate nonzero-baseline recovery edge need checking. |
| **N-4 / Note** | Dust LP redemption can burn shares for no asset payout | Reject zero/zero redemption, regression | Source-level remedy present; independent EVM rerun outstanding. |
| **N-5 / Note** | `dMax` overflow path and impossible `dFloor > WAD` config | Overflow-safe rate limit and constructor gate bounds | Source-level remedy present; independent bounded integer-model checks passed. |
| **N-6 / Note** | Stale NatSpec; extreme arithmetic cases | Documentation corrected; remaining arithmetic behavior dispositioned | Comment corrected; no universal-input proof claimed. |

**N-1/N-2:** The chosen demo configuration makes the kappa rate limit nonbinding; the developer documented its rationale and added an empirical four-year sweep. The sweep uses a dedicated opt-in test setting and **does not run under ordinary `forge test`**.

**N-3:** Non-nesting-safe liquidity lock remains a conditional maintenance risk, with no reachable exploit established in the described current call order. **N-7:** Standard ERC-20 and native-ETH supported-token policy documented; nonstandard tokens are not generally supported. **N-8:** Cross-block MEV, adversarial JIT liquidity and sequencer ordering remain open economic questions.

## Remediation trace

- [Original reviewed commit](https://github.com/Prakhar-30/POINCARE/commit/78d75e24d7a899fbd488aedd0c0d4de6fe019adb)
- [Nine-commit remediation comparison](https://github.com/Prakhar-30/POINCARE/compare/78d75e24d7a899fbd488aedd0c0d4de6fe019adb...7699f62630404a34fd89298f8994cdc63c9da1ab)
- [Developer's remediation notes](https://github.com/Prakhar-30/POINCARE/blob/sfs_labs_audit_work/SECURITY.md)
- [Regression test source](https://github.com/Prakhar-30/POINCARE/blob/sfs_labs_audit_work/test/regression/ShsLabsFindings.t.sol)

The developer reports 240 passing Foundry tests on the changed branch. During the follow-up, the available GitHub status showed **Vercel success but no independent Foundry CI confirmation** for the reviewed head. Therefore the second assessment was explicitly **conditional source-level remediation analysis, not independently verified EVM test sign-off**. The developer's prior Unichain Sepolia deployment predates the changes and cannot be treated as proof of the new bytecode.

## What I contributed

1. Defined a review against an **exact code revision** and the developer's specified threat model.
2. Delivered precise, prioritised findings with code locations, consequences, remediation options and testable acceptance criteria.
3. Independently reproduced the original tests and triaged complementary static/property-based evidence.
4. Traced the maintainer's subsequent real code changes and new regression cases, instead of treating a claim of a fix as proof.
5. Delivered a second, separate technical follow-up that distinguishes implemented changes from unverified test outcomes and unresolved integrations.

**Takeaway:** A useful security review is not just a vulnerability list. Its professional value also includes traceable remediation, reproducible evidence and an explicit boundary between *fixed in source*, *tested*, and *verified for deployment*.

## Attribution and disclosure

This case study describes my **personal technical work** under the SFS.Labs portfolio identity. It is not an official POINCARÉ audit badge or a representation that a security firm certified the protocol. The client's public code and documentation are linked as independent supporting sources. The original confidential report, private evidence bundle, email correspondence and wallet details are **not published**.

**Contact / work:** [GitHub](https://github.com/SFS-Labs) · [LinkedIn](https://www.linkedin.com/in/mathias-steinbach-513869446/) · [X](https://x.com/sfs_labs)
