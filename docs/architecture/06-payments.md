# Payments and money movement

Wasl never stores card data and treats the payment provider as replaceable. The provider is not chosen yet because it depends on the target country, so the design fixes the interface and leaves the vendor open. See [open questions](../open-questions.md).

- **Provider interface.** One `PaymentProvider` protocol with four operations: create checkout, parse and verify webhook, refund, pay out. The MVP ships one implementation plus a fake provider for local development and tests.
- **Hosted checkout only.** The donor pays on the provider's page, which keeps Wasl at the lightest card-security tier (PCI DSS SAQ A).
- **Ledger.** Each paid donation writes balanced entries: provider clearing account to cause balance, with any fee to a fee account. Disbursements and refunds write reversing entries. Balances are always derived from entries.
- **Fees.** Wasl takes no cut and the cause absorbs provider fees, shown to the donor before payment (assumed).
- **Refunds.** Admin-only, full amount, within the provider's refund window, and only while the money is undisbursed.
- **Currency.** One currency per cause, set at creation. No conversion in the MVP.
- **Payout account.** Payouts go to the verified account of the presenter or their organisation. When the presenter is not the beneficiary, the proof-of-use update must show the money reaching the beneficiary.
- **Reconciliation.** A nightly job compares each cause's cached raised amount with the ledger and alerts on any difference.

## Custody

The larger open question is whether donations settle into a Wasl account and are paid out, or go directly to the presenter through a marketplace-style split.

Holding funds enables staged release and proof-of-use gating, but may require a licence or a registered charity structure. The flows in these docs assume Wasl holds funds (assumed). Legal advice is needed before the donations module is built against a real provider.
