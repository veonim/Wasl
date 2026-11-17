# Decisions

A dated log of what has been decided, and a list of the assumptions that stand until someone confirms or changes them.

## How to use this file

- Add a decision when a design choice is made or changed. Newest at the bottom, numbered `D-NNN`.
- Status is **Decided** (confirmed by the product owner) or **Proposed** (chosen in the design, not yet reviewed).
- When a decision replaces an earlier one, mark the earlier one "Superseded by D-NNN". Do not delete it.
- When an assumption is confirmed or changed, move it from the assumptions table into the log.

## Log

| ID | Date | Decision | Status | Affects |
| --- | --- | --- | --- | --- |
| D-001 | 2026-11-16 | Stack is a FastAPI backend and a Next.js frontend. | Decided | [system](architecture/01-system.md) |
| D-002 | 2026-11-16 | The interface is in English and Urdu, with right-to-left layout from the first release. | Decided | [languages](architecture/04-languages.md) |
| D-003 | 2026-11-16 | The trust graph is the primary trust system. A donor sees how they are connected, through people they trust, to the presenter of a cause. Trust is shown relative to the viewer, with no public score. | Decided | [trust model](product/03-trust-model.md) |
| D-004 | 2026-11-16 | A donor with no connections sees every cause and can give on a second layer of trust: documents, case information and the presenter's history of previous cases. | Decided | [trust model](product/03-trust-model.md) |
| D-005 | 2026-11-16 | The first legitimate cases are seeded through connectors. The product supports this with: presenter separate from beneficiary, assisted submission, introduced-by, shareable cause links. | Decided | [seeding](product/04-seeding.md) |
| D-006 | 2026-11-16 | The docs in this repository are the source of truth. `CLAUDE.md` is the anchor. Development is tracked module by module in `docs/development/`. | Decided | [docs index](README.md) |
| D-007 | 2026-11-16 | PostgreSQL is the database, with Redis for queue and rate limiting and a modular-monolith API. | Proposed | [system](architecture/01-system.md) |
| D-008 | 2026-11-16 | The trust graph is stored in PostgreSQL and searched with a bidirectional breadth-first search inside the API, not in a separate graph database. | Proposed | [system](architecture/01-system.md) |
| D-009 | 2026-11-16 | Payments go through hosted checkout behind a `PaymentProvider` interface, with a double-entry append-only ledger. | Superseded by D-013 | none |
| D-010 | 2026-11-16 | The role is named "presenter" everywhere, in code, routes and docs. "Beneficiary" is the person in need. | Proposed | all |
| D-011 | 2026-11-16 | The visual design follows the SUMMIT glassmorphism reference: navy `#0c1420`, pale blue `#e8eef8`, steel `#8fa4c4`, warm glow `#ffd9a0`, Georgia type, glass surfaces with backdrop blur. Answers Q-10. | Decided | [design](design/README.md), [reference](design/reference.md) |
| D-012 | 2026-11-17 | Graphs are real graphs: rendered from API data with a computed layout, interactive (pan, zoom, path highlighting, selection, expansion). A static drawing is not acceptable in the build. The canvas graphs are style placeholders only. | Decided | [design language](design/design-language.md#graphs), [M3](development/modules/M3-trust-and-checks.md) |
| D-013 | 2026-11-17 | **Core design: no money flows through Wasl.** Donors give directly to the presenter's own account, outside Wasl. Wasl never processes, holds or routes money: no payment provider, checkout, balance, payout, refund or fee. It shows checked payment details and records gifts that donors report and presenters confirm. Supersedes D-009; closes Q-02 and Q-03. | Decided | [giving](architecture/06-giving.md), all modules |

## Standing assumptions

Each of these was chosen to keep the design moving. None is confirmed. Each must be a configuration value or an easily changed rule, not a constant spread through the code.

| ID | Assumption | Related question |
| --- | --- | --- |
| A-01 | Trust paths are searched up to three links deep. | Q-11 |
| A-02 | Trust links have three levels: know them, trust them, would vouch by name. | Q-11 |
| A-03 | A new account cannot vouch at the top level for its first 30 days. | Q-11 |
| A-04 | Staff checks of identity and payment details are required before any cause goes Live, underneath the graph. | Q-12 |
| A-05 | Trust links are visible only to the person trusted and to people who trust the link's author. | Q-14 |
| A-06 | When a vouched cause is closed for fraud, vouchers and affected donors are notified and the failed vouch stays visible to those who trust the voucher. | Q-15 |
| A-07 | Proof of use is due every 30 days while a cause is Live with confirmed gifts, and within 30 days of closing or reaching the goal. | Q-26 |
| A-08 | Verification lapses after 12 months. | Q-08 |
| A-09 | Three open reports pause a cause and hide its payment details. | Q-08 |
| A-10 | Only gifts the presenter confirms count toward a cause's total. | Q-25 |
| A-11 | Payment details are visible to anyone on a Live cause, and hide automatically when the goal is reached. | Q-24, Q-27 |
| A-12 | A guest can see payment details and record a gift without an account. | Q-09 |
| A-13 | Case documents are published only by the presenter's choice, redacted of personal identifiers. | Q-16 |
| A-14 | Presenter history covers only cases run on Wasl. | Q-17 |
| A-15 | Submission is invitation-only at launch, and connectors are not paid per case. | Q-21 |
