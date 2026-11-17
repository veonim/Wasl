# M5 Reporting and administration

**Status:** Not started
**Depends on:** M4
**Blocked by:** nothing. Shaped by Q-08, Q-15, Q-26.

## Goal

A presenter proves how the money they received was used, donors are told, a missed report has visible consequences, and staff have one console to run the platform.

## Read first

- [Flows](../../product/02-flows.md), flow 4
- [Giving: no money flows through Wasl](../../architecture/06-giving.md), rules and "when something goes wrong"
- [Trust model](../../product/03-trust-model.md), keeping the graph honest
- [Data model](../../architecture/02-data-model.md), Causes and Giving sections
- [Design language](../../design/design-language.md). Screens: `PresenterDashboard`, `GiftsProof`, `Admin`, `TrustStates` in [design](../../design/README.md)

## Tasks

### API

- [ ] `M5-T01` Proof-of-use update: period covered, amount accounted for, attachments, translations; must show money reaching the beneficiary when presenter and beneficiary differ
- [ ] `M5-T02` Proof-of-use schedule from configuration: interim while Live with confirmed gifts, final after closing or reaching the goal
- [ ] `M5-T03` Reminder emails before each deadline
- [ ] `M5-T04` Missed deadline: hide payment details, flag the cause for review, mark the presenter's history
- [ ] `M5-T05` Notify donors who recorded a gift of each update, in their language
- [ ] `M5-T06` Closing a cause: goal met, ended by the presenter, or closed by an admin; final-state rules
- [ ] `M5-T07` Failed vouch: when a cause is closed for fraud, notify by-name vouchers and the donors who recorded gifts, and mark the failed vouch on the voucher's record
- [ ] `M5-T08` Barring a presenter from presenting again
- [ ] `M5-T09` Admin endpoints: users, causes, reports, disputed gifts, payment-method changes, audit log, suspend and close
- [ ] `M5-T10` Data export and deletion request workflow

### Web

- [ ] `M5-T11` Presenter: proof-of-use form with deadline, amounts confirmed and accounted for
- [ ] `M5-T12` Updates timeline on the cause page; presenter history reflects on-time proof of use
- [ ] `M5-T13` Admin console: users, causes, reports with pause state, disputed gifts, payment-method changes, audit log viewer
- [ ] `M5-T14` Failed-vouch notice shown to people who trust the voucher

### Tests

- [ ] `M5-T15` Deadline logic: interim and final proof of use, and the missed-deadline consequences
- [ ] `M5-T16` End-to-end, flow 4: confirm gifts, post proof of use, donors notified; and the missed-deadline path
- [ ] `M5-T17` Closing for fraud notifies exactly the by-name vouchers and the donors who recorded gifts

## Acceptance

- [ ] A presenter can post proof of use covering the gifts they confirmed
- [ ] A missed deadline hides the payment details and shows on the presenter's history
- [ ] Donors are told of each update
- [ ] Closing a cause for fraud notifies vouchers and donors and marks the failed vouch
- [ ] Every admin action appears in the audit log
- [ ] Nothing in the console moves, holds or returns money

## Notes

Nothing yet.
