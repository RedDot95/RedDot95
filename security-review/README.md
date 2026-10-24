# Independent Solidity review methodology

This describes an evolving manual pre-launch code-review practice. It is a process and reporting structure, not evidence that a client review has been completed or that every technique below has already been applied to a real engagement.

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

Client identities, relationships, code, findings, reports and testimonials are published only with explicit permission. Until then, public portfolio material contains methodology and blank templates only. An active review elsewhere is not duplicated or managed in this repository.

## Evidence register

No client reference or completed-review claim is published here. Add a reference only after delivery and disclosure permission, including the reviewed commit, agreed scope, date, limitations and permitted report link.
