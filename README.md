# SFS.Labs
### Applied AI implementation · workflow automation · research operations

I'm Mathias Steinbach, a Finance & Capital Markets student at TH Köln, building practical systems at the intersection of financial research, data quality and AI-assisted development.

My main focus is **Applied AI Implementation, Enterprise Automation and AI Operations**: connecting inputs, validation, review and useful outputs. I am interested in working-student roles where I can help implement and operate these workflows.

## Selected work

| Project | What to inspect | Current scope |
|---|---|---|
| **[SFS Genomics — AI-Native Genomic Intelligence Platform](https://sfs-labs.gitbook.io/sfs-labs-docs/ai-docs/featured-engineering-project-sfs-genomics/sfs-genomics)** | [Live mobile interface](https://sfs-labs.github.io/lagoon/), [source + CI](https://github.com/SFS-Labs/lagoon/pull/1), 607k-call EU Cloudflare data pipeline, OAuth PKCE/DCR remote MCP for ChatGPT, scientific validation gates | Authenticated end-to-end workflow and 256-shard D1 reconciliation verified; five-locus research validation pilot; **not** clinically validated. Genomics source currently on a separate feature branch in the legacy lagoon repository |
| [AI Knowledge Operations Lab](https://github.com/SFS-Labs/ai-knowledge-ops-lab) | Source-linked SEC disclosure pipeline, auditable model-output import, review controls, regression tests and recorded replay | M1 working research milestone; 15-source rules replay and separate 3-source AI-assisted demonstration. Labels and model quality remain unvalidated |
| [Value Rail](https://github.com/SFS-Labs/value-rail-mvp) | CoinGate clearance ingestion, deterministic offer filtering, persisted signal feed and optional worker/UI | Evolving monitoring MVP; source availability, actual delivery and commercial outcomes are separate concerns |
| [POINCARÉ — Solidity Security Review](security-review/case-studies/poincare-2026.md) | Independent scoped review of 7 Solidity files; 2 Low findings, 8 Notes; developer remediation and separate source-level follow-up | Delivered Oct 2026; 222 original Foundry tests independently reproduced; follow-up fixes examined, 240 revised tests maintainer-reported only |

These projects grow from ongoing interests. Their READMEs distinguish implemented behavior, observed verification and planned work.

## How I work with AI

I define the problems, requirements and development direction. Copilot and other AI assistants contribute implementation, review, tests and documentation; project-level attribution and Git history show the evidence. AI-generated code still requires verification. A commit under my account does not by itself mean that every line was manually written by me.

## Additional specialization: Solidity security reviewing

I am building an **independent manual pre-launch review practice** alongside my AI/automation work. The focus is explicit scope, reproducible reasoning, actionable findings and clear limitations.

- [Review methodology](security-review/README.md)
- [Scope template](security-review/SCOPE_TEMPLATE.md)
- [Finding and report format](security-review/REPORT_TEMPLATE.md)

**Delivered client reference:** [POINCARÉ — Security Review to Remediation](security-review/case-studies/poincare-2026.md) (October 2026). The review is commit-pinned, limited in scope, and includes a separate remediation source assessment. It is **not** a firm audit, certification, complete economic-security assessment or mainnet safety guarantee.

---

**SFS.Labs is the display identity of this personal portfolio.** The GitHub account is [SFS-Labs](https://github.com/SFS-Labs), migrated from RedDot95 on 24 October 2026.
