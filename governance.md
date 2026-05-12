# Q-SAG Substrate Governance

**AIXYBER TECH LTD** and the **Q-SAG Open Source Substrate Programme**.

This document describes the current governance model of the Q-SAG substrate, who holds decision-making authority, and how the model is intended to evolve as the substrate matures.

We are being explicit and honest about the current state. The substrate is at an early stage. Pretending otherwise would not build trust.

---

## Current state (May 2026)

The Q-SAG substrate is currently a **single-maintainer project**, stewarded by AIXYBER TECH LTD.

| Role | Holder |
|------|--------|
| Sole maintainer | Muhammad Zaid Naeem |
| Steward entity | AIXYBER TECH LTD (UK Company No. 16826340) |
| Decision-making authority | Sole director of AIXYBER TECH LTD |
| Signing key for releases | GPG `A65AF5B7F02C9EB5B98023D70DB861BBF30F0D7B` |

All public Q-SAG substrate repositories are owned by the [`Neoxyber` GitHub account](https://github.com/Neoxyber). This account is owned and controlled by AIXYBER TECH LTD.

---

## What this means in practice

- All commits, releases, and policy decisions are reviewed and authorised by a single person.
- There is no quorum, no committee, and no formal review board at this time.
- The maintainer's GPG-signed Git commit is the binding statement of authorship and review.
- Pull requests from external contributors are welcomed, but final merge authority rests with the maintainer.
- Security disclosure response, release cadence, and policy updates are bounded by the time of a single person.

We believe this is the right model for a substrate at this stage. It allows decisions to be made quickly, the architectural vision to remain coherent, and the project to ship work. It also has clear limitations: single point of failure, no multi-party review of cryptographic decisions, and bus-factor of one.

We are open about this. As the substrate matures and external adoption justifies it, the model will change.

---

## Contributor verification ladder

External participation is welcomed at four levels, each with proportionate trust and access. This ladder is intentionally low-friction at the entry point.

### Level 1 — Reviewer (no account needed)

Anyone can read the public substrate, file security disclosures via the channels in [`coordinated-disclosure.md`](./coordinated-disclosure.md), and quote or build on the documentation under CC-BY-4.0.

No GitHub account required. No identity verification. The reporter's chosen identity is honoured.

### Level 2 — Drive-by contributor

A first-time pull request author:

- Must have a GitHub account with 2FA enabled.
- Must include a DCO `Signed-off-by:` trailer on each commit.
- Does not need to GPG-sign commits at this level; the maintainer's signed merge preserves the verification chain.
- No additional verification required.

This is the easiest entry point. It is intentionally close to zero friction.

### Level 3 — Recurring contributor

A contributor who has had multiple PRs merged and demonstrates sustained engagement may be invited to:

- GPG-sign their own commits with a published key.
- Be listed in a substrate-repository `MAINTAINERS.md` file with their fingerprint.
- Receive Write permission on specific repositories.

This is by invitation, based on observed work, not a self-application process.

### Level 4 — Co-maintainer

When the substrate has more than one co-maintainer (target: late 2027 onward, dependent on adoption), governance shifts to:

- A documented quorum requirement (target: 2-of-N) for material decisions affecting release contents, breaking API changes, or security policy.
- Each co-maintainer's signing key documented in `MAINTAINERS.md`.
- A `GOVERNANCE.md` per repository describing the local decision process.
- A formal `CODE_OF_CONDUCT.md` enforcement path.

This level does not yet exist on the substrate. It will be created when there is more than one maintainer with sustained involvement, not before.

---

## Family participation

Family members of the maintainer may contribute to the substrate. We disclose this openly because it is relevant to governance.

Specific rules apply:

- A family member cannot be the sole maintainer of the same library as the sole director of AIXYBER TECH LTD, without a non-family third-party co-maintainer also having merge authority.
- Pull requests from family contributors are reviewed by a non-family reviewer where practical.
- Family contribution is unpaid open-source work. AIXYBER TECH LTD does not pay family members for substrate contributions.
- Family relationships are disclosed in `MAINTAINERS.md` against each name.
- University-affiliated student work (e.g. dissertation projects) requires the student's institution to be aware of the substrate involvement, and ideally an independent co-supervisor.

These rules exist to keep the substrate's review chain credible to external auditors and to protect family members from conflict-of-interest concerns.

---

## Relationship to AIXYBER TECH LTD's commercial work

AIXYBER TECH LTD also delivers commercial services under the trading name **Neoxyber**. The substrate and the commercial work are governed differently:

| Surface | Governance |
|---------|-----------|
| Q-SAG substrate (open source) | This document — open contributor ladder, Apache 2.0 / CC-BY-4.0, DCO. |
| Neoxyber commercial services | Normal commercial confidentiality and contract terms. Not governed by this document. |

A future legal subsidiary, **Neoxyber Services Ltd**, will be incorporated to hold the commercial work when revenue justifies it. The substrate will remain under AIXYBER TECH LTD until migration to a foundation.

---

## Migration to a foundation

The Q-SAG substrate is intended, in the long run, to live under a neutral software foundation rather than a private company.

Candidates we are tracking:

- **Linux Foundation Europe** — domiciled in Brussels, well-positioned for EU CRA alignment.
- **NLnet Foundation / Commons Conservancy** — Dutch foundations supporting open-source commons projects, including those at SME scale.
- **A purpose-built Stichting** — Dutch foundation form, used by projects like Let's Encrypt's ISRG.

A migration will happen when at least two of the following are true:

- The substrate has more than one sustained maintainer.
- At least two external organisations have adopted substrate libraries in production.
- A funding pathway exists to support the foundation's operating costs.
- AIXYBER TECH LTD's commercial work has been incorporated separately (as Neoxyber Services Ltd), so the substrate's migration does not entangle commercial concerns.

Until migration, AIXYBER TECH LTD is the trademark holder, copyright assignee for AIXYBER TECH LTD-authored code, and substrate steward. External contributors retain their own copyright via DCO; there is no Contributor Licence Agreement (CLA).

The substrate is permanently Apache 2.0. There is no plan to relicense to a more restrictive licence (BSL, SSPL, etc.) under any circumstances. This commitment is documented here for the public record.

---

## Updating this document

Material changes to governance — new maintainers, foundation migration, contributor ladder changes — are reflected in commits to this file and announced in repository release notes.

The previous version of this document is always retrievable from the Git history of `governance.md`.

---

_Policy effective: 12 May 2026. Reviewed annually or on material change._

© 2026 AIXYBER TECH LTD. Released under the Creative Commons Attribution 4.0 International License (CC-BY-4.0).
