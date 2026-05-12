# The Q-SAG Open Source Substrate Programme

**Stewarded by AIXYBER TECH LTD.**

The Q-SAG programme is a set of open-source cryptographic and audit primitives for AI-agent governance. The acronym stands for **Quantum-Secure Autonomous Gateway**.

This document is an overview. It is not a reference manual or a specification — those live in the individual library repositories. It is intended for someone landing on the substrate for the first time and asking "what is this and why does it exist?"

---

## What problem is the substrate solving?

Two trends are colliding:

1. **Cryptographic agility is becoming urgent.** Quantum computing has progressed to the point where current public-key cryptography has a finite shelf life. NIST has finalised post-quantum standards (ML-KEM, ML-DSA, SLH-DSA) and the industry is migrating. This migration requires substrate-level primitives that downstream applications can adopt without rebuilding their cryptography stacks.

2. **AI agents are operating with increasing autonomy.** Systems that make decisions, take actions, and communicate with each other need a way to be governed. Audit trails, evidence chains, identity attestations, and rollback-resistant logs are no longer optional. They need to be standard primitives, not bespoke implementations.

The Q-SAG substrate provides the primitives that sit at the intersection of these two trends: post-quantum cryptography, audit chains, and governance infrastructure for AI-agent systems.

It is **substrate, not application**. The programme intentionally does not build the user-facing AI agent. It builds the cryptographic and audit foundation that AI agents (and adjacent systems) can be built on top of.

---

## What "open-source substrate" actually means

We use "substrate" rather than "platform" or "framework" deliberately. The distinction matters:

- A **platform** typically implies a hosted service, runtime, or environment.
- A **framework** typically implies an opinionated structure that applications conform to.
- A **substrate** is a foundation layer of independent primitives that downstream projects compose freely.

The Q-SAG substrate is the third. Each library in the substrate is independently usable, independently versioned, and free to be adopted (or not adopted) on its own. There is no single "Q-SAG runtime" you install. There is a library you depend on for canonical JSON serialisation, another for post-quantum signatures, another for Postgres-backed audit chains, and so on.

This composability is deliberate. It maximises adoption (downstream users take only what they need), maximises auditability (small libraries with clear scope are easier to review), and minimises lock-in.

---

## Substrate libraries

The full programme is planned as ten libraries. Each is at a different stage of maturity. We are explicit about the current state of each.

### Cryptographic primitives

| Library | Subject | Current stage |
|---------|---------|---------------|
| `qsag-canonical` | RFC 8785 strict JSON canonicalisation | Scaffolded; v0.1 in active implementation |
| `qsag-pq-primitives` | Post-quantum signing and KEM wrappers (ML-DSA, ML-KEM, SLH-DSA, Falcon) | Scaffolded; v0.1 in active implementation |
| `qsag-anchors` | Verifiable anchors and Merkle trees for audit chains | Scaffolded; v0.1 in active implementation |
| `qsag-confidential` | Confidential computing primitives (SEV-SNP, TDX, attestation) | Planned |

### Audit infrastructure

| Library | Subject | Current stage |
|---------|---------|---------------|
| `pg-qsag-audit` | Postgres extension for tamper-evident audit logs (TLE + pgrx) | In active implementation; renaming from `pg_qsag_audit` |
| `qsag-evidence` | Evidence chain and lineage tracking | Planned |
| `qsag-cascade` | Multi-party rollback-resistant log replication | Planned |

### AI-agent governance

| Library | Subject | Current stage |
|---------|---------|---------------|
| `qsag-aibom` | AI Bill of Materials (AI-BOM) generation and verification | Planned |
| `qsag-ocsf` | OCSF-aligned event mappings for AI-agent activity | Planned |
| `qsag-coalition` | Multi-agent identity attestation and coordination | Planned |

The library set is intentionally not closed. As the substrate evolves and external contributors propose additions, new libraries may join. None will be added without clear scope, named maintainer, and adherence to the standards in [`governance.md`](./governance.md).

---

## Honest gap statement

The substrate is at an early stage. As of May 2026:

- **Three libraries are in active implementation:** `qsag-canonical`, `qsag-pq-primitives`, and `qsag-anchors`. None have reached v0.1 yet.
- **One library is in active implementation under a renaming:** `pg-qsag-audit` (formerly `pg_qsag_audit`, with the SQL identifier `qsag_audit` retained).
- **Six libraries are planned but not yet started.**
- **No library has been externally audited.** External audits will be conducted before any v1.0 release, with public reports.
- **No library has been adopted in production by external organisations** that we are aware of. The substrate is a research-grade artefact today, not a production-grade dependency.

We are stating this clearly because the trust we hope to earn over time can only be built by being honest about where we are right now. Anyone evaluating the substrate for adoption should weigh this gap statement against their own risk tolerance and timeline.

---

## What we are not building

To avoid confusion, the Q-SAG programme is **not**:

- A blockchain or distributed ledger. The audit primitives use cryptographic anchoring, but the substrate has no token, no consensus protocol, and no on-chain economics.
- A managed service. The substrate is libraries you depend on, not a hosted product. AIXYBER TECH LTD does offer commercial support and integration services under the Neoxyber trading name, but the substrate itself is purely open source.
- A complete AI agent framework. Other excellent projects exist for that. The substrate provides primitives those frameworks can be built on, not the framework itself.
- A regulatory compliance product. The substrate provides primitives useful for compliance (audit chains, evidence trails, AI-BOM), but compliance with EU AI Act, ISO/IEC 42001, NIST AI RMF, or any specific regulation requires a complete system, not just substrate primitives.

---

## Why this exists at AIXYBER TECH LTD

AIXYBER TECH LTD is a London-based research and technology company (Companies House No. 16826340), founded in late 2025. The substrate is the company's primary research output.

The choice to develop substrate openly, under Apache 2.0, and with a migration path toward a neutral foundation, is deliberate:

- **Cryptographic infrastructure must be auditable.** Closed-source cryptography is rejected by serious users for good reason. Public substrate is the only path to long-term trust.
- **Open-source positioning aligns with public funding pathways.** Programmes like NLnet's NGI Zero Commons Fund, Sovereign Tech Fund, and Alpha-Omega support open-source security primitives.
- **A small UK SME cannot credibly run cryptographic infrastructure as a commercial product.** A larger foundation, with multi-party maintainership and independent audits, is the right long-term home. Stewarding the substrate now and migrating later is the path that gets there.

The commercial services side of AIXYBER TECH LTD (trading as Neoxyber) is a separate matter. Substrate is open. Services are commercial. The two are deliberately decoupled.

---

## How to engage with the substrate

| You are... | Suggested first step |
|------------|---------------------|
| A researcher interested in PQ or AI governance | Read the substrate library READMEs and the ADRs in each library's `docs/decisions/` directory |
| A potential user evaluating the substrate | Read this document, then `governance.md`, then the specific library you are interested in. Treat the gap statement above as honest input to your decision. |
| A security researcher | Read [`coordinated-disclosure.md`](./coordinated-disclosure.md) and report findings to `security@aixybertech.com` |
| A potential contributor | Read `governance.md` for the contributor ladder, then look at open issues on a substrate repository |
| A journalist or analyst | The maintainer is reachable at `zaidnaeem@aixybertech.com` |
| A funder or grant programme | Programme overview here; budget and milestones available on request |
| A regulator | This document plus [`coordinated-disclosure.md`](./coordinated-disclosure.md) and [`AI_ASSISTANCE.md`](./AI_ASSISTANCE.md) form the substrate's public-policy disclosure surface |

---

## Versioning of this overview

This document is versioned via Git history in this repository. It will be updated as substrate maturity changes — particularly the library stage table above.

---

_Document effective: 12 May 2026. Reviewed quarterly or on material change._

© 2026 AIXYBER TECH LTD. Released under the Creative Commons Attribution 4.0 International License (CC-BY-4.0).
