# Roadmap

Six modules, built in order. Each ends in something a person can click through. No module handles money: donors give directly to presenters (decision D-013).

| Module | Delivers | Depends on | Status | Blocked by |
| --- | --- | --- | --- | --- |
| [M1 Foundation](modules/M1-foundation.md) | Repo scaffold, CI, design tokens and base components, sign-up and sign-in, roles, English and Urdu shell | none | Not started | none |
| [M2 Causes](modules/M2-causes.md) | Submission, assisted submission, public listing, cause page with the case record, share previews | M1 | Not started | none |
| [M3 Trust graph and baseline checks](modules/M3-trust-and-checks.md) | Trust links, path search, a real interactive graph, trust panel, My network; verifier queue, cause lifecycle, audit log | M2 | Not started | Q-12, Q-14 |
| [M4 Giving](modules/M4-giving.md) | Checked payment details on the cause page, recording a gift, presenter confirmation, totals, acknowledgements | M3 | Not started | none |
| [M5 Reporting and administration](modules/M5-reporting-and-admin.md) | Proof of use and its deadlines, failed-vouch notices, admin console | M4 | Not started | none |
| [M6 Launch readiness](modules/M6-launch-readiness.md) | Security review, accessibility, load test, backups, legal pages, pilot | M5 | Not started | Q-18, Q-19, Q-20, Q-22 |

## Why this order

- M1 before everything: every later module needs accounts, roles, both languages and the design tokens.
- M2 before M3: the graph needs causes and presenters to point at, and the case record is the trust layer that works with zero connections.
- M3 before M4: payment details show only on Live causes, a recorded gift stores the trust path the donor saw, and payment methods need a reviewer.
- M4 before M5: there is nothing to account for until gifts are recorded and confirmed.

## After the MVP

Not planned in detail. Candidates are listed under "Later" in [the overview](../product/01-overview.md).
