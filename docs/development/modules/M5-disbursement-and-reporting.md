# M5 Disbursement and reporting

**Status:** Not started
**Depends on:** M4
**Blocked by:** Q-03 (custody). If funds go straight to the presenter, this module changes shape. Shaped by Q-08, Q-15.

## Goal

Raised money reaches the presenter's verified account under admin approval, the presenter proves how it was used, and staff have one console to run the platform.

## Read first

- [Flows](../../product/02-flows.md), flow 4
- [Payments and money movement](../../architecture/06-payments.md)
- [Trust model](../../product/03-trust-model.md), keeping the graph honest
- [Data model](../../architecture/02-data-model.md), Money and Causes sections

## Tasks

### API

- [ ] `M5-T01` `disbursement` table; presenter requests a payout of some or all of the available balance
- [ ] `M5-T02` Admin approve and reject; payout through the provider interface; reversing ledger entries
- [ ] `M5-T03` Proof-of-use update tied to a disbursement, with attachments and translations; must show money reaching the beneficiary when presenter and beneficiary differ
- [ ] `M5-T04` Deadline from configuration; reminder emails before it; a missed deadline blocks further payouts and flags the cause for review
- [ ] `M5-T05` Notify donors of each update, in their language
- [ ] `M5-T06` Refunds: admin-only, full amount, only while undisbursed, with reversing ledger entries
- [ ] `M5-T07` Failed vouch: when a cause is closed for fraud, notify by-name vouchers and the donors who gave through their paths, and mark the failed vouch on the voucher's record
- [ ] `M5-T08` Closing a cause: goal met or ended; final state rules
- [ ] `M5-T09` Admin endpoints: users, causes, reports, disbursements, audit log, suspend
- [ ] `M5-T10` Data export and deletion request workflow

### Web

- [ ] `M5-T11` Presenter: balance, payout request, proof-of-use form, deadline countdown
- [ ] `M5-T12` Updates timeline on the cause page; presenter history now reflects on-time proof of use
- [ ] `M5-T13` Admin console: users, causes, disbursement approvals, reports, refunds, audit log viewer
- [ ] `M5-T14` Failed-vouch notice shown to people who trust the voucher

### Tests

- [ ] `M5-T15` Ledger tests for payout, partial payout and refund
- [ ] `M5-T16` End-to-end, flow 4: request, approve, post proof of use, donor notified; and the missed-deadline path

## Acceptance

- [ ] A presenter can request a payout and an admin can approve it, and the ledger balances afterwards
- [ ] A payout can never exceed the available balance
- [ ] A missed proof-of-use deadline blocks the next payout and flags the cause
- [ ] Donors are told of each update
- [ ] Closing a cause for fraud notifies vouchers and affected donors
- [ ] Every admin action appears in the audit log
- [ ] A refund is refused once the money has been disbursed

## Notes

Nothing yet.
