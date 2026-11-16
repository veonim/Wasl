# Roadmap

Six modules, built in order. Each ends in something a person can click through.

| Module | Delivers | Depends on | Status | Blocked by |
| --- | --- | --- | --- | --- |
| [M1 Foundation](modules/M1-foundation.md) | Repo scaffold, CI, sign-up and sign-in, roles, English and Urdu shell | none | Not started | none |
| [M2 Causes](modules/M2-causes.md) | Submission, assisted submission, public listing, cause page with the case record, share previews | M1 | Not started | none |
| [M3 Trust graph and baseline checks](modules/M3-trust-and-checks.md) | Trust links, path search, trust panel and graph, My network; verifier queue, cause lifecycle, audit log | M2 | Not started | Q-12, Q-14 |
| [M4 Donations](modules/M4-donations.md) | Checkout, webhooks, ledger, receipts, donor history | M3 | Not started | Q-01, Q-02, Q-03 for the real provider; the fake provider is unblocked |
| [M5 Disbursement and reporting](modules/M5-disbursement-and-reporting.md) | Payout requests and approvals, proof-of-use updates, failed-vouch notices, admin console | M4 | Not started | Q-03 |
| [M6 Launch readiness](modules/M6-launch-readiness.md) | Security review, accessibility, load test, backups, legal pages, pilot | M5 | Not started | Q-18, Q-19, Q-20, Q-22 |

## Why this order

- M1 before everything: every later module needs accounts, roles and both languages.
- M2 before M3: the graph needs causes and presenters to point at, and the case record is the trust layer that works with zero connections.
- M3 before M4: a donation records the trust path the donor saw, and only Live causes can take donations.
- M4 before M5: there is nothing to disburse until donations exist.

## After the MVP

Not planned in detail. Candidates are listed under "Later" in [the overview](../product/01-overview.md).
