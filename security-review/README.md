# Independent Solidity review methodology

This describes an evolving independent, scope-limited manual pre-launch review practice. The [POINCARÉ client case study](case-studies/poincare-2026.md) documents one completed review, the developer's remediation and a separate source-level follow-up, including explicit verification limits. Methodology below is not proof that every technique was applied to every engagement.

## Review lifecycle

1. **Agree scope:** repository, immutable commit, included files/contracts, compiler/tool versions, chain assumptions, external dependencies, trust model, exclusions and delivery terms. Use the [scope template](SCOPE_TEMPLATE.md).
2. **Understand the system:** document assets, roles, privileged actions, upgrade paths, call/data flow and intended invariants. Treat specifications and tests as claims to check against code.
3. **Manual review:** trace state transitions and external interactions; examine authorization, initialization, accounting/rounding, reentrancy, token behavior, oracle/economic assumptions and upgrade/storage risks where applicable. Prioritize the actual design rather than claiming exhaustive checklist coverage.
4. **Validate observations:** record exact file/line/commit evidence and minimal reproducible examples. Use existing tests or isolated local reproductions when useful. Mark untested hypotheses as unconfirmed. No live exploitation, handling of client funds or production changes.
5. **Report:** separate confirmed findings, unresolved questions and informational notes. Explain impact, required conditions, likelihood rationale, remediation and limitations.
6. **Retest separately:** bind any remediation assessment to a new exact commit and list what was rechecked. Initial delivery never implies later changes are covered.

## Findings discipline

Use [the report template](REPORT_TEMPLATE.md). High/medium/low labels require a written impact and feasibility rationale; severity is contextual, not a numerical guarantee. Document tool/AI assistance and distinguish manual reasoning, automated output and independently reproduced evidence. Do not upload private source or findings to external tools without the agreed permission.

## Commercial and disclosure boundaries

The initial offer is a manual pre-launch review without upfront payment, with voluntary compensation after receipt of the report. Actual scope, timing, confidentiality, usage rights and delivery terms must be agreed for each engagement. No certification, formal audit-firm status, insurance, exhaustive vulnerability coverage or security guarantee is claimed.

Client identities, relationships, code, findings, reports and testimonials are published only within the permission and confidentiality boundaries agreed for each engagement. Confidential client deliverables and private evidence bundles are not hosted here.

## Evidence register

- **POINCARÉ (October 2026):** [Public case study](case-studies/poincare-2026.md) — seven scoped Solidity files, two Low findings, eight informational observations, and a second source-level review of the maintainer's nine remediation commits. Original review and follow-up are pinned to distinct revisions; the fixed branch's 240 tests were maintainer-reported, **not independently rerun**.

Each public case should identify the exact reviewed revision, agreed scope, methods, limits, developer work versus reviewer work, and any outstanding conditions.
