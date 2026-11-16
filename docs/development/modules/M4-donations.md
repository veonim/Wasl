# M4 Donations

**Status:** Not started
**Depends on:** M3
**Blocked by:** Q-01 (country), Q-02 (provider) and Q-03 (custody) for the real provider. Everything up to `M4-T10` runs on the fake provider and is unblocked. Shaped by Q-06, Q-09.

## Goal

A donor can give to a Live cause, the money is recorded in a ledger that always balances, and the donor gets a receipt.

## Read first

- [Payments and money movement](../../architecture/06-payments.md)
- [Flows](../../product/02-flows.md), flow 2
- [Data model](../../architecture/02-data-model.md), Money section
- [API](../../architecture/03-api.md)

## Tasks

### API

- [ ] `M4-T01` `PaymentProvider` protocol: create checkout, parse and verify webhook, refund, pay out; fake provider with a local hosted-checkout page
- [ ] `M4-T02` `donation` table; `POST /donations` creates a pending donation and returns a checkout URL; guest and signed-in donors
- [ ] `M4-T03` Store the trust path the donor was shown on the donation
- [ ] `M4-T04` `payment_event` table; webhook endpoint with signature check and idempotency by event ID
- [ ] `M4-T05` `ledger_entry` table, append-only by database permission; balanced entries for each paid donation including fees
- [ ] `M4-T06` Update the cause's cached raised amount; nightly reconciliation job that alerts on any mismatch
- [ ] `M4-T07` Only Live causes accept donations; a Paused cause refuses them
- [ ] `M4-T08` Receipt email in the donor's language; receipt endpoint
- [ ] `M4-T09` `GET /me/donations`; anonymous-to-public flag
- [ ] `M4-T10` Rate limit on donation creation; webhook retry handling in the worker
- [ ] `M4-T11` Real provider implementation against its sandbox (blocked by Q-01, Q-02, Q-03)

### Web

- [ ] `M4-T12` Donate panel on the cause page: amount, fee shown before payment, anonymous option
- [ ] `M4-T13` Return pages for success, failure and cancel
- [ ] `M4-T14` Donor history page with receipts
- [ ] `M4-T15` Progress bar and raised amount on listing and cause pages

### Tests

- [ ] `M4-T16` Ledger tests: every flow leaves the ledger balanced; a replayed webhook changes nothing
- [ ] `M4-T17` End-to-end, flow 2, on the fake provider, as guest and as signed-in donor, in both locales

## Acceptance

- [ ] A guest and a signed-in donor can each complete a donation on the fake provider
- [ ] The donor receives a receipt in their language
- [ ] The cause total rises by exactly the donated amount, and the ledger balances
- [ ] Sending the same webhook twice does not double-count
- [ ] A donation to a cause that is not Live is refused
- [ ] The reconciliation job reports zero mismatches after a test run
- [ ] With the real provider: a sandbox payment completes end to end

## Notes

Nothing yet.
