# Coordinated Disclosure Policy

**AIXYBER TECH LTD** and the **Q-SAG Open Source Substrate Programme**.

This is the full coordinated disclosure policy. The short-form pointer for automated tooling is at [`security.txt`](./security.txt) (RFC 9116). The cryptographic key for confidential reports is at [`pgp-key.txt`](./pgp-key.txt).

---

## How to report

### Email (preferred)

Send a report to **`security@aixybertech.com`**.

Where possible, encrypt the body with the PGP public key in [`pgp-key.txt`](./pgp-key.txt).

```
Fingerprint: A65A F5B7 F02C 9EB5 B980  23D7 0DB8 61BB F30F 0D7B
Long ID:     0DB861BBF30F0D7B
Primary UID: Muhammad Zaid Naeem (AIXYBER TECH LTD) <zaidnaeem@aixybertech.com>
```

If you cannot encrypt, send unencrypted email and we will respond with a key fingerprint verification to begin an encrypted channel.

### What to include

The more of the following you include, the faster we can act. Missing items do not invalidate a report.

- Affected substrate library or repository (e.g. `qsag-canonical`, `pg-qsag-audit`)
- Affected version, commit hash, or release tag
- Type of issue (e.g. cryptographic weakness, RCE, supply-chain, parser bug, side channel)
- Step-by-step reproduction or proof of concept
- Impact assessment in your view
- Whether the issue is currently known publicly anywhere
- A contact channel for follow-up (email, Signal, Matrix — your choice)
- Your preferred name for acknowledgment (or "anonymous")

### Do not

- Do not file a public GitHub issue, pull request, or discussion describing the vulnerability.
- Do not post on social media until a coordinated release date has been agreed.
- Do not test against production systems of third parties using our substrate; restrict testing to your own systems.

---

## Scope

### In scope

- All public Q-SAG substrate repositories under [`github.com/Neoxyber`](https://github.com/Neoxyber).
- The AIXYBER TECH LTD corporate website at `aixybertech.com` and `*.aixybertech.com`.
- The Neoxyber commercial website at `neoxyber.com` and `*.neoxyber.com`.
- Released artefacts on PyPI, crates.io, npm, Docker Hub, or GitHub Container Registry under the `aixybertech`, `neoxyber`, or `qsag` namespaces.
- Documentation files in this `aixybertech-well-known` repository where errors could materially mislead a researcher (for example, a wrong PGP fingerprint).

### Out of scope

- Third-party libraries we depend on. Report those to the upstream maintainers; if relevant to substrate users, we will coordinate.
- Self-hosted forks or modifications outside our control.
- Issues purely affecting outdated browsers, missing security headers without demonstrable impact, or theoretical issues without a working proof of concept.
- Social engineering of AIXYBER TECH LTD staff, contractors, or family members.
- Physical attacks against AIXYBER TECH LTD premises or personnel.
- Denial of service attacks against our infrastructure.

---

## Response timeline

We aim for the following timeline. These are targets, not contractual guarantees. We are currently a single-maintainer project; response times will improve as the team grows.

| Stage | Target |
|-------|--------|
| Initial acknowledgment that the report was received | 72 hours |
| Initial assessment (severity, scope confirmation) | 7 days |
| Substantive response (action plan or initial fix) | 30 days |
| Coordinated public disclosure | 90 days from initial report, by default |

If a report is being actively exploited in the wild, we will move faster and prioritise emergency releases.

If 90 days is genuinely insufficient (for example, because a fix requires coordinated multi-party rollout), we will negotiate an extension with the reporter in good faith and document the reason publicly at disclosure time.

If we have not responded within 7 days, please escalate by:

1. Sending a follow-up to `security@aixybertech.com`.
2. Sending a copy to `zaidnaeem@aixybertech.com` (sole director, until further notice).

---

## What we will do

- Acknowledge your report.
- Investigate in good faith.
- Provide regular updates while a fix is in progress.
- Credit you in [acknowledgments](#acknowledgments) at disclosure time, with the name or handle you prefer (or keep you anonymous if you prefer).
- Publish a clear post-mortem when the fix is released, including:
  - What went wrong
  - The fix
  - Mitigations available before upgrade
  - Lessons learned and process changes

## What we will not do

- We do not run a bug bounty programme. We do not pay for reports. If your organisation can pay you for the time spent on a report, we are grateful for your work either way.
- We do not retaliate against good-faith security research conducted under this policy.
- We do not require non-disclosure agreements before discussing a vulnerability.
- We do not threaten legal action against researchers acting in good faith under this policy. Please see [Safe harbour](#safe-harbour) below.

---

## Safe harbour

We consider good-faith security research conducted in accordance with this policy to be:

- Authorised access to our systems and code within the scope above.
- Exempt from civil action by AIXYBER TECH LTD for activities consistent with this policy.
- Compliant with our terms of service, where the activity is otherwise covered by this policy.

We will not pursue, support, or escalate legal claims, including those under the UK Computer Misuse Act 1990 or analogous laws, against researchers who:

- Make a good-faith effort to avoid privacy violations, data destruction, or service degradation.
- Report the vulnerability privately before any public disclosure.
- Comply with the timelines and procedures in this document.
- Do not exploit the vulnerability beyond the minimum required to demonstrate it.

If a third party brings a legal action against you for research conducted under this policy, we will, where reasonable, make a public statement that the research was authorised. We cannot bind third parties (other affected projects, governments, or platforms), but we will say what we can.

This safe harbour statement is offered in good faith. It does not waive your responsibilities under applicable law.

---

## Cryptographic disclosure

For issues affecting cryptographic primitives (post-quantum schemes in `qsag-pq-primitives`, audit-chain constructions in `qsag-anchors` or `pg-qsag-audit`, canonicalisation in `qsag-canonical`), we ask that reporters allow additional time where appropriate, since:

- Independent cryptographic review may be needed before a fix is final.
- Algorithm-level breaks may require coordination with the broader cryptographic community.
- Some fixes require version-rotation rather than patches.

We will be transparent about extensions of the 90-day window for cryptographic issues and will explain the rationale at disclosure time.

---

## AI-assisted research

We accept reports based on AI-assisted analysis, including outputs from automated scanners, large language models, and agent-based security tooling. Please clearly mark the report as AI-assisted, and where possible verify the finding yourself before reporting. We will not dismiss AI-assisted reports out of hand, but we ask reporters to confirm reproducibility independently because false positives are common.

If a finding turns out to be a hallucination or false positive, we appreciate the effort and will say so politely. There is no penalty.

---

## Acknowledgments

We gratefully acknowledge the researchers who have helped improve the security of AIXYBER TECH LTD and the Q-SAG substrate. Names appear with the consent of each researcher.

_No disclosures have been made under this policy yet. This section will grow as the substrate matures._

If you would like your name added here following a coordinated disclosure, indicate this in your report.

---

## Policy versioning

This policy is versioned via Git history in this repository. Material changes are reflected in updates to:

- The `Expires` field in [`security.txt`](./security.txt).
- The footer date below.

The previous version of this policy can always be retrieved from the Git history of `coordinated-disclosure.md`.

---

## Contact summary

| Channel | Address |
|---------|---------|
| Primary security inbox | `security@aixybertech.com` |
| Director escalation | `zaidnaeem@aixybertech.com` |
| PGP key | [`pgp-key.txt`](./pgp-key.txt) |
| Fingerprint | `A65A F5B7 F02C 9EB5 B980  23D7 0DB8 61BB F30F 0D7B` |

---

_Policy effective: 12 May 2026. Reviewed annually._

© 2026 AIXYBER TECH LTD. Released under the Creative Commons Attribution 4.0 International License (CC-BY-4.0).
