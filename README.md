# SFS.Labs
### AI Solutions · Automation · Systems Integration · Technical Delivery

I'm Mathias Steinbach. I work at the intersection of business requirements, AI-assisted software implementation, integration architecture, and evidence-led engineering. My academic background is Finance & Capital Markets (B.Sc., TH Köln, ongoing); my practical background includes technical customer onboarding and hands-on development direction across cloud, data, security, and agent-tool integrations.

**Current focus:** paid, real-world B2B AI implementations with direct customer and engineering-team exposure — from discovery and requirements through APIs, testing, deployment and operations. I am open to junior, associate and technically substantive entry roles; the **work** matters more than the title.

## How I approach engineering

I don't treat tool fluency or a plausible demo as deployment evidence. I prefer short feedback loops:

1. **Frame the actual problem:** identify user outcomes, operating context, data boundaries and acceptance criteria.
2. **Design the full path:** connect inputs, validation, authentication, persistence, tool interfaces and observable outputs.
3. **Build with AI assistance where appropriate:** coordinate implementation, inspect changes and establish repeatable tests rather than assume generated code is correct.
4. **Investigate failures at the affected layer:** reproduce, isolate the root cause and update the surrounding architecture or operational harness when necessary.
5. **Re-verify the end-to-end behavior:** separate CI success, client interoperability, data correctness and live-service availability.
6. **Record the remaining limitations:** document what was observed, what is inferred and what remains untested.

**Concrete example:** In SFS Genomics, an OAuth discovery conflict, Cloudflare D1 read-quota exhaustion, mobile-file constraints and a source-repository migration each required a different engineering response. The resulting project records separate acceptance evidence for persistence, protected MCP client calls, OAuth protocol checks and bounded scientific validation.

## Selected engineering and delivery evidence

| Work | What it demonstrates | Verified scope |
| --- | --- | --- |
| **[SFS Genomics](https://github.com/SFS-Labs/sfs-genomics)** · [engineering study](https://sfs-labs.gitbook.io/sfs-labs-docs/ai-docs/featured-engineering-project-sfs-genomics/sfs-genomics) | iPhone browser import → EU Cloudflare D1 → OAuth PKCE/DCR → authenticated remote MCP / ChatGPT integration → public GWAS/Ensembl evidence checks | 607,051 SNP calls reconciled over 256 D1 partitions; recorded authenticated client calls; scoped CI and five-locus reference QC. Not clinical-grade or guaranteed continuously available. |
| **[SFS Education Funding](https://sfs-labs.gitbook.io/sfs-labs-docs/ai-docs/featured-engineering-project-sfs-education-funding/sfs-education-funding)** | TypeScript Worker, scheduled collection, source provenance, versioned documents, pass/fail/unknown rules, seven bounded MCP tools | Deployed engineering prototype with 725 stored documents and 2,025 claims at the dated checkpoint; **zero** verified application-ready programs. [Source repository](https://github.com/SFS-Labs/education-funding-mcp) currently private. |
| **[POINCARÉ review](security-review/case-studies/poincare-2026.md)** | External scoped Solidity review, independently reproduced test suite, actionable developer findings and source-level remediation follow-up | Two low-severity findings, eight notes; 222 original Foundry tests independently reproduced. Maintainer's revised-suite result not independently rerun. |
| **[Value Rail](https://github.com/SFS-Labs/value-rail-mvp)** | Source adapter, state change detection, scheduled JSON feed, optional worker, deterministic testing | 326 offline tests at a documented checkpoint; successful CI/feed runs, no claim of current profit or phone delivery. |
| **[AI Knowledge Ops Lab](https://github.com/SFS-Labs/ai-knowledge-ops-lab)** | Real SEC-source ingestion, input hashing, auditable model-output import, review routing and reproducible quality checks | 15 development sources, separate three-source AI-assisted replay and 32 regression tests. No validated production model benchmark. |

## Working with AI tools

I define the problem, technical boundaries, requirements and acceptance evidence. I use AI-assisted development with explicit review, tool-calling workflows, CI, and defect reproduction to accelerate implementation. Code and commit attribution alone do not establish that every line was authored manually. I distinguish **implemented**, **tested**, and **observed in operation**.

### Skills evidenced by the projects
- **Integration:** REST/API design, OAuth 2.0, PKCE, MCP, Cloudflare Workers, D1/KV, GitHub Actions and source control.
- **Implementation:** AI-assisted Python/JavaScript/TypeScript, validation pipelines, deterministic tests, data-model boundaries and error semantics.
- **Delivery:** customer issue analysis, requirements capture, acceptance criteria, reproducible verification, documentation and technical trade-offs.

## Professional development

- **MIT Professional Education:** Applied Agentic AI for Organizational Transformation (70 hours, completed May 2026).
- **Oracle:** Building Agentic Workflows for Fusion Applications using Oracle AI Agent Studio (16 hours, completed March 2026).
- **ACAMS:** Certified Cryptoasset Anti-Financial Crime Specialist (CCAS, September 2025).
- **TH Köln:** B.Sc. Finance and Capital Markets, ongoing since September 2025.

## Links

- [Published technical documentation](https://sfs-labs.gitbook.io/sfs-labs-docs/)
- [LinkedIn](https://www.linkedin.com/in/mathias-steinbach-513869446/)
- [Contact](mailto:mathias.steinbach@icloud.com)

**SFS.Labs** is the public display identity for personal engineering work associated with **Sigma Finance Systems**. It is not a claim of an incorporated company, paid enterprise deployments or an independently operated security-audit firm.
