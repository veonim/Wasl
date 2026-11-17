# Giving: no money flows through Wasl

**Core rule (decision D-013): Wasl never processes, holds or routes money.** A donor gives directly to the presenter, outside Wasl, using the presenter's own bank account or mobile wallet. Wasl shows who to trust and how to pay them, and keeps a record of what people say was given and received.

This is a property of the whole product, not a setting. No feature may introduce a payment through Wasl.

## What this removes

- No payment provider, checkout, card handling or webhooks
- No Wasl bank account, balance, payout or disbursement
- No refunds: Wasl cannot return money it never held
- No platform fee taken from a gift
- No ledger of money held. Wasl keeps a record of reported gifts, which is information, not accounting.

## How giving works

1. **The presenter lists how to be paid.** One or more payment methods in their own name, or their organisation's: a bank account, a mobile wallet. A reviewer checks that the account title matches the presenter's verified identity before the cause goes Live.
2. **The donor sees the details on the cause page.** They appear only while the cause is Live. They are hidden when the cause is Paused, Closed or has reached its goal.
3. **The donor pays directly**, from their own bank or wallet app. Wasl is not involved in the transfer.
4. **The donor tells Wasl they gave** (optional): amount, date, method and the transfer reference. The trust path they were shown is stored with it.
5. **The presenter confirms receipt**, or marks the gift as not received. They can also add gifts that arrived without being recorded, so the total stays honest.
6. **The cause total is the sum of confirmed gifts.** Gifts reported but not yet confirmed are shown separately.
7. **The presenter posts proof of use.** See the rule below.

## Rules

- **Payment details are checked and locked.** Changing a payment method hides the details and sends the change to a reviewer. This is the main defence against someone swapping in their own account.
- **Details always show the account title**, so the donor can match the name in their banking app against the presenter's name on Wasl.
- **The headline figure is confirmed money only.** A donor's unconfirmed report never counts toward the goal.
- **Reaching the goal hides the payment details** (assumed), so a cause does not keep collecting past what it asked for. The presenter can reopen with a new goal through review.
- **Proof of use is due** within 30 days of the cause closing or reaching its goal, and at least every 30 days while the cause is Live and holds confirmed gifts not yet reported on (assumed). When the presenter is not the beneficiary, it must show the money reaching the beneficiary.
- **A missed proof of use** hides the payment details, flags the cause for review, and shows on the presenter's history.
- **Disputes.** If a donor says they gave and the presenter says nothing arrived, the gift is marked disputed and an admin can look at both sides. Wasl can record the outcome; it cannot move money.
- **Acknowledgement, not receipt.** When a presenter confirms a gift, Wasl emails the donor an acknowledgement. It is not a tax receipt and says so.
- **Amounts** are stored as integer minor units with a currency code. One currency per cause.

## What Wasl can do when something goes wrong

Wasl has no money to withhold or return. Its levers are information and visibility:

- Pause a cause, which hides its payment details at once
- Close a cause for fraud
- Notify every donor who recorded a gift, and everyone who vouched for the presenter by name
- Mark the failed vouch on vouchers' records and the closed case on the presenter's history
- Bar the presenter from presenting again

This is why the trust graph, the case record and the baseline checks carry the whole weight of the product. See the [trust model](../product/03-trust-model.md).

## Still to confirm

- Which payment methods a presenter may list depends on the target country (Q-01, Q-23).
- Whether a platform that only publishes payment details still falls under fundraising or payment rules needs legal review (Q-22).
- How Wasl funds itself with no fee on gifts (Q-06).
