# M4 Giving

**Status:** Not started
**Depends on:** M3
**Blocked by:** nothing. Shaped by Q-09, Q-23, Q-24, Q-25; build against the defaults in [decisions.md](../../decisions.md).

## Goal

A donor can see how to pay a presenter directly, record that they gave, and see the cause total rise once the presenter confirms. No money passes through Wasl at any point.

## Read first

- [Giving: no money flows through Wasl](../../architecture/06-giving.md), all of it
- [Flows](../../product/02-flows.md), flow 2
- [Data model](../../architecture/02-data-model.md), Giving section
- [API](../../architecture/03-api.md), giving rules
- [Design language](../../design/design-language.md). Screens: `Main` (give card), `RecordGift`, `DonorHistory`, `GiftsProof` in [design](../../design/README.md)

## Tasks

### API

- [ ] `M4-T01` `payment_method` table; presenter adds, edits and removes methods; any change sets status to pending review and writes to the audit log
- [ ] `M4-T02` Verifier review of a payment method: account title against the presenter's verified identity, with a proof document
- [ ] `M4-T03` `GET /causes/{slug}/payment-details`: returns details only for a Live cause whose methods have all passed review; rate-limited
- [ ] `M4-T04` Hide payment details automatically when a cause is Paused, Closed, has a method under review, or reaches its goal (from configuration)
- [ ] `M4-T05` `gift` table; `POST /causes/{slug}/gifts` records a gift as reported, for guests and signed-in donors, storing the trust path shown
- [ ] `M4-T06` Presenter confirms a gift, marks it not received, or adds a gift that arrived unrecorded
- [ ] `M4-T07` Cause totals: `confirmed amount` from confirmed gifts only, `reported amount` from unconfirmed ones; recomputed by a worker job
- [ ] `M4-T08` Disputed gifts: admin list and a resolve action that records an outcome
- [ ] `M4-T09` Acknowledgement email to the donor on confirmation, in their language, stating it is not a tax receipt
- [ ] `M4-T10` `GET /me/gifts`; anonymous-to-public flag; donor can withdraw an unconfirmed report
- [ ] `M4-T11` Rate limits on recording gifts and on payment-detail lookups

### Web

- [ ] `M4-T12` Give card on the cause page: confirmed total and progress, the statement that Wasl does not handle money, payment details with account title and copy buttons, and the "I have given" action
- [ ] `M4-T13` Record-a-gift form and its confirmation state
- [ ] `M4-T14` Donor history: gifts, how the donor was connected, whether the presenter confirmed, proof-of-use status
- [ ] `M4-T15` Presenter: payment methods screen, and the list of gifts to confirm
- [ ] `M4-T16` Progress and confirmed amount on listing and cause pages

### Tests

- [ ] `M4-T17` A reported gift never changes the confirmed total; confirmation does; a confirmed amount cannot be edited
- [ ] `M4-T18` Payment details are unreachable for causes that are not Live, and after any method change until re-review
- [ ] `M4-T19` End-to-end, flow 2: view details, record a gift as guest and as signed-in donor, presenter confirms, total updates, in both locales

## Acceptance

- [ ] A donor can see a Live cause's payment details with the account title
- [ ] Payment details disappear the moment a cause is paused, closed, reaches its goal, or a method is edited
- [ ] A guest and a signed-in donor can each record a gift
- [ ] The cause total rises only when the presenter confirms, by exactly the confirmed amount
- [ ] The donor receives an acknowledgement in their language
- [ ] No code path creates a payment, charge, balance, payout or refund
- [ ] Every payment-method change appears in the audit log

## Notes

Nothing yet.
