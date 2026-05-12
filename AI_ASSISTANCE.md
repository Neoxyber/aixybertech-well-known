# AI Assistance Disclosure

**AIXYBER TECH LTD** and the **Q-SAG Open Source Substrate Programme**.

This is the canonical AI-assistance disclosure policy for the substrate. Substrate repository `CONTRIBUTING.md` files reference this document rather than duplicating it.

---

## Plain statement

AIXYBER TECH LTD uses AI assistance — specifically large language model agents, currently Claude (Anthropic) — in the design, implementation, review, and documentation of substrate code and policy. This use is disclosed openly because we believe transparency about tooling is a precondition for trust in security-critical open-source work.

All substrate output, regardless of how it was assisted, is reviewed and signed off by a human maintainer. The maintainer's GPG-signed Git commit and DCO `Signed-off-by` trailer are the legally binding statement that the maintainer has reviewed, understood, and takes responsibility for the work.

---

## What AI assistance does in this project

- Drafts code, documentation, ADRs, commit messages, and policy text from human-provided requirements.
- Generates test cases, fuzz harnesses, and known-answer test vectors from specifications.
- Reviews maintainer-written code for bugs, edge cases, and style consistency.
- Helps trace through cryptographic protocols and verify they match referenced specifications.
- Drafts release notes, changelog entries, and project planning documents.

## What AI assistance does not do

- AI assistance does not autonomously commit to any substrate repository. Every commit on every public substrate repository is reviewed and authorised by a human maintainer.
- AI assistance does not have access to private signing keys, HSMs, or release-signing infrastructure.
- AI assistance does not make final decisions about cryptographic primitives, security trade-offs, or policy positions. Those are maintainer decisions.
- AI assistance does not represent AIXYBER TECH LTD to external parties (researchers, contributors, journalists, regulators). All such communication is by a human.

---

## Disclosure in commit history

Substrate commits where AI assistance was substantial include a `Assisted-by:` trailer in the commit message body, immediately before the DCO `Signed-off-by:` trailer. Example:

```
feat(qsag-canonical): add RFC 8785 strict mode

Implements strict RFC 8785 JSON canonicalisation with no
silent fallback to alternative serialisations. See ADR-L1-002
for the rationale.

Assisted-by: Claude (Anthropic), under maintainer review and DCO sign-off.
Signed-off-by: Muhammad Zaid Naeem <zaidnaeem@aixybertech.com>
```

Trivial AI assistance (such as autocomplete, single-line refactors, or rephrasing a docstring) is not separately disclosed. The threshold for `Assisted-by:` is **substantial drafting or analysis** that materially shaped the commit's content.

The maintainer's signature on the commit is the binding statement; the `Assisted-by:` trailer is informational, for downstream auditors and historians of the project.

---

## Legal and standards framing

We have considered the following frameworks in deciding to disclose AI assistance openly and to retain maintainer responsibility for all output:

| Framework | Relevance |
|-----------|-----------|
| EU AI Act (Regulation (EU) 2024/1689), Art 2(6) | Open-source research and development activity is carved out of most operational obligations. Substrate work falls within this carve-out. |
| EU Cyber Resilience Act (CRA) | The CRA evaluates the security properties of the artefact (the substrate library), not the authorship process. AI-assisted code is evaluated on the same basis as fully hand-written code. |
| ISO/IEC 42001 (AI Management System Standard) | Anticipates organisational use of AI assistance and provides governance language; AIXYBER TECH LTD will pursue evidence-supplier alignment with this standard as the substrate matures. |
| DCO (Developer Certificate of Origin) v1.1 | The DCO `Signed-off-by` trailer is the maintainer's statement of responsibility for the contribution. AI assistance does not weaken or invalidate the DCO. |
| Apache License 2.0 | Copyright in code contributed to substrate repositories is held by AIXYBER TECH LTD per the UK Copyright, Designs and Patents Act 1988 s.11(2). AI-assisted output is not a separate copyright work. |

These frameworks are referenced for transparency. They do not constitute legal advice and may evolve. The policy will be updated as the regulatory landscape changes.

---

## What this means for substrate contributors

If you submit a pull request to a substrate repository:

- You may use AI assistance for your own work. Disclose it via the `Assisted-by:` trailer where appropriate.
- Your DCO `Signed-off-by:` line is your statement that you have reviewed and take responsibility for the contribution, regardless of how much AI assistance was involved.
- We will not reject a contribution because it was AI-assisted. We will reject contributions that contain unverified output, hallucinated APIs, or pasted material that the contributor does not understand.

If you report a security vulnerability:

- AI-assisted reports are accepted. See [`coordinated-disclosure.md`](./coordinated-disclosure.md) for details.

---

## Questions

Questions about this policy can be sent to `info@aixybertech.com` for general inquiries or `zaidnaeem@aixybertech.com` directly. Process improvements or specific policy concerns can also be filed as issues on the [`aixybertech-well-known`](https://github.com/Neoxyber/aixybertech-well-known) repository.

---

## Versioning

This policy is versioned via Git history in this repository. Material changes will be reflected in a date update below and noted in commit messages.

---

_Policy effective: 12 May 2026. Reviewed annually._

© 2026 AIXYBER TECH LTD. Released under the Creative Commons Attribution 4.0 International License (CC-BY-4.0).
