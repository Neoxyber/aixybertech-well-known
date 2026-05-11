# aixybertech-well-known

Canonical reference files for **AIXYBER TECH LTD** and the **Q-SAG Open Source Substrate Programme**.

This repository serves a single purpose: hold the authoritative, single-source-of-truth versions of files that other AIXYBER and Q-SAG repositories reference. Rather than copying these documents into every substrate library (where they would drift over time), each library carries a short pointer back to the canonical version here.

This pattern is modelled on similar approaches used by other open-source projects (notably Supabase's `well-known` repository) and on the RFC 9116 `.well-known/` convention for security disclosure.

---

## Files

| File | Subject |
|------|---------|
| [`company-facts.md`](./company-facts.md) | Corporate identity, registered details, contact channels |
| [`pgp-key.txt`](./pgp-key.txt) | PGP public key for verifying security communications |
| [`security.txt`](./security.txt) | RFC 9116 coordinated disclosure metadata |
| [`coordinated-disclosure.md`](./coordinated-disclosure.md) | Full coordinated disclosure policy |
| [`AI_ASSISTANCE.md`](./AI_ASSISTANCE.md) | AI assistance disclosure policy |
| [`governance.md`](./governance.md) | Current governance model |
| [`substrate-programme.md`](./substrate-programme.md) | Q-SAG substrate programme overview |
| [`secure-by-design.md`](./secure-by-design.md) | CISA Secure by Design pledge status |

---

## Public web surface

Where appropriate, files in this repository are also served from the AIXYBER TECH LTD website at the standard RFC 9116 location:

```
https://aixybertech.com/.well-known/security.txt
https://aixybertech.com/.well-known/pgp-key.txt
```

The canonical version always lives here in this repository. The web surface is a mirror.

---

## Reporting a security issue

Please do not file public GitHub issues for security vulnerabilities.

See [`coordinated-disclosure.md`](./coordinated-disclosure.md) for the full policy.

In short: email `security@aixybertech.com`, encrypted with the PGP key in [`pgp-key.txt`](./pgp-key.txt) (fingerprint `A65A F5B7 F02C 9EB5 B980  23D7 0DB8 61BB F30F 0D7B`).

---

## Licensing

This repository uses dual licensing:

- **Code** (any scripts, configuration files, automation): Apache License, Version 2.0. See [`LICENSE`](./LICENSE).
- **Documentation** (markdown files, text policies, prose): Creative Commons Attribution 4.0 International (CC-BY-4.0). See [`LICENSE-DOCS`](./LICENSE-DOCS).

You are free to redistribute, quote, translate, or build on these documents. We ask only that attribution be retained per the CC-BY-4.0 terms.

---

## About AIXYBER TECH LTD

AIXYBER TECH LTD is a London-based research and technology company stewarding the **Q-SAG (Quantum-Secure Autonomous Gateway) Open Source Substrate Programme** — open primitives for post-quantum cryptography, audit chains, and AI-agent governance.

Commercial services are delivered under our trading name **Neoxyber**. This repository concerns the open-source substrate side only.

- Website: <https://aixybertech.com>
- Substrate code: <https://github.com/Neoxyber>
- Company No: 16826340 · Registered in England and Wales
- Registered office: 48 Warwick Street, London, England, W1B 5AW

---

© 2026 AIXYBER TECH LTD. Released under the Apache License, Version 2.0 (code) and CC-BY-4.0 (documentation).
