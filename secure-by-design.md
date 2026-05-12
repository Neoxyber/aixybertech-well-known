# Secure by Design — Status

**AIXYBER TECH LTD** and the **Q-SAG Open Source Substrate Programme**.

This document tracks AIXYBER TECH LTD's alignment with the [CISA Secure by Design pledge](https://www.cisa.gov/securebydesign/pledge), a voluntary commitment by software manufacturers to seven security-improvement goals.

---

## Status summary

**AIXYBER TECH LTD has not yet signed the CISA Secure by Design pledge.**

We intend to sign before the public v0.1 release of the substrate. Signing requires the substrate to demonstrably meet enough of the seven goals that the commitment is credible rather than aspirational.

This document tracks our progress against each goal. Each goal is labelled:

- **Met** — the goal is genuinely achieved across the substrate today.
- **Partial** — the goal is met in some libraries or processes, not all.
- **Planned** — the goal is in the work plan but not yet implemented.

Stages are reviewed at each substrate library v0.1 release and at the programme level quarterly.

---

## Goal 1 — Multi-factor authentication

> _"Increase the use of multi-factor authentication across the manufacturer's products."_

Substrate libraries are not user-facing products; they are primitives. The MFA goal as written applies to vendor administrative surfaces, not substrate primitives.

For the AIXYBER TECH LTD vendor surface:

- GitHub account (`Neoxyber`) has 2FA enforced on all accounts with access.
- Cloudflare account (holding `aixybertech.com`, `neoxyber.com`, `neoxyber.co.uk`) has 2FA enforced on all Super Administrator and Administrator accounts.
- Microsoft 365 tenant (`aixybertech.com` and `neoxyber.com`) has MFA enforced on all accounts.
- 1Password vault for AIXYBER TECH LTD secrets requires MFA.

Status: **Met** for AIXYBER TECH LTD vendor surface. Substrate libraries themselves do not have a user authentication surface.

---

## Goal 2 — Default passwords

> _"Reduce default passwords."_

Substrate libraries do not ship with default credentials. Configuration that requires secrets (signing keys, database connection strings) is loaded from the deployer's environment.

The `pg-qsag-audit` Postgres extension does not create database users or set passwords; it operates as a Postgres extension within the deployer's existing security context.

Status: **Met.**

---

## Goal 3 — Reducing entire classes of vulnerability

> _"Reduce entire classes of vulnerability across the manufacturer's products."_

The substrate's design choices target the elimination of specific vulnerability classes:

- **Memory safety:** substrate libraries are implemented in Rust where the implementation language is a choice. The pgrx flavour of `pg-qsag-audit` is Rust-backed. Python-based wrappers (where present, for ergonomics) call into Rust or audited C implementations.
- **Cryptographic agility:** the substrate enables algorithm rotation by configuration rather than code change, reducing the cost of responding to a future cryptanalytic break.
- **Strict serialisation:** `qsag-canonical` enforces RFC 8785 strict mode with no silent fallback, eliminating an entire class of canonicalisation-divergence bugs.
- **Type-safe interfaces:** library APIs are typed end-to-end; ambiguous untyped data structures are avoided.
- **Dependency minimisation:** substrate libraries depend only on well-maintained upstream cryptographic libraries (the NIST PQC reference implementations, RustCrypto, the WC3 JCS reference vectors).

Status: **Partial.** The design choices are made; the implementation has not reached full v0.1 across all libraries, so the elimination is not yet demonstrably complete.

---

## Goal 4 — Security patches

> _"Increase the installation of security patches by customers."_

The substrate does not have "customers" in the consumer-software sense; it has downstream library consumers. The goal here is to make patching as low-friction as possible:

- Semantic versioning is followed strictly. Security patches are released as patch-level updates wherever the API contract permits.
- Substrate libraries are published to the platform-standard registries (PyPI, crates.io, etc.), enabling normal dependency-update workflows.
- Security advisories are published via GitHub Security Advisories and announced through the disclosure channel in [`coordinated-disclosure.md`](./coordinated-disclosure.md).
- The `pg-qsag-audit` Postgres extension follows Postgres extension versioning conventions, allowing in-place upgrades within a Postgres major version.

Status: **Partial.** The release infrastructure is being built; no library has released a security patch yet because no library has had a public v0.1 release.

---

## Goal 5 — Vulnerability disclosure policy

> _"Publish a vulnerability disclosure policy that authorises testing in good faith and commits to not pursuing legal action."_

A full coordinated disclosure policy is published at [`coordinated-disclosure.md`](./coordinated-disclosure.md), with RFC 9116 metadata at [`security.txt`](./security.txt).

The policy:

- Authorises good-faith security research within a defined scope.
- Commits to safe harbour, with explicit language addressing the UK Computer Misuse Act 1990.
- Defines response timeline targets (acknowledgment, assessment, fix, coordinated public disclosure).
- Accepts AI-assisted research with a reproducibility ask.

Status: **Met.**

---

## Goal 6 — CVEs

> _"Demonstrate transparency in vulnerability reporting via CVE issuance."_

AIXYBER TECH LTD will become a CVE Numbering Authority (CNA) for substrate-owned vulnerabilities, or operate via a recognised CNA-of-last-resort, once the substrate has had at least one public release. Until then:

- Vulnerabilities affecting substrate libraries will be assigned CVEs via GitHub's CNA-LR pathway for issues in GitHub-hosted open-source code.
- CVE records will be published with technical detail sufficient for downstream library consumers to assess impact, alongside the GitHub Security Advisory.
- Vulnerabilities affecting upstream dependencies will be reported to those projects and noted in our advisories where downstream substrate users may be affected.

Status: **Planned.** Will become **Partial** with the first public substrate release; **Met** when AIXYBER TECH LTD operates as a CNA or has documented CVE-issuance practice across multiple disclosures.

---

## Goal 7 — Evidence of intrusion

> _"Provide customers with evidence of intrusions affecting the product."_

The audit-chain libraries in the substrate (`pg-qsag-audit`, `qsag-anchors`, `qsag-evidence`, `qsag-cascade`) are specifically designed to produce tamper-evident records suitable for forensic investigation. For substrate libraries used as primitives, the goal is upstream evidence support:

- The audit-chain primitives, when adopted by a downstream system, give that system the cryptographic foundation to detect and prove intrusions.
- The substrate itself is library code, not a hosted product. The hosted-product version of this goal applies to deployers who adopt the substrate, not to AIXYBER TECH LTD.

For the AIXYBER TECH LTD vendor surface:

- GitHub provides audit logs for repository-level actions.
- Cloudflare provides audit logs for DNS, account, and edge-rule actions.
- Microsoft 365 provides audit logs for tenant-level actions.

Status: **Partial.** The substrate's intent is to make this goal easier for downstream adopters. The vendor surface has standard cloud-provider audit logging.

---

## Trigger conditions to sign the pledge

We intend to formally sign the CISA Secure by Design pledge when **all** of the following are true:

1. At least three substrate libraries have had a public v0.1 release.
2. Goals 5 (disclosure policy) and 6 (CVE issuance practice) are at "Met" status.
3. Goal 3 (vulnerability classes) is at least "Partial" with documented evidence.
4. The signing process has been reviewed by a non-AIXYBER-TECH-LTD party (e.g. a NLnet contact, a substrate adopter, or a CISA representative).

Until then, this document tracks status. Signing the pledge before the substrate can credibly back the commitment would be inconsistent with the substrate's framing of intellectual honesty about gaps.

---

## Versioning

This document is reviewed at each substrate library v0.1 release and updated to reflect the current state of each goal. Updates are visible via the Git history of `secure-by-design.md`.

---

_Document effective: 12 May 2026. Next review: at first substrate library v0.1, or 12 August 2026, whichever is sooner._

© 2026 AIXYBER TECH LTD. Released under the Creative Commons Attribution 4.0 International License (CC-BY-4.0).
