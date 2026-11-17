# Key flows

Four flows carry the MVP. Each one ends in a record the others can rely on. No money moves through Wasl in any of them; see [giving](../architecture/06-giving.md).

## 1. A donor checks trust

1. Hamza presents a cause. Bilal, who knows him, sets his trust in Hamza to *would vouch by name*.
2. Ayesha, who trusts Bilal but has never met Hamza, opens the cause.
3. The API searches for paths from Ayesha to Hamza, up to three links, and returns only links Ayesha is entitled to see.
4. The trust panel shows "You trust Bilal. Bilal would vouch for Hamza." and draws the path as a graph.
5. Ayesha can ask Bilal directly outside Wasl, then decides whether to give.

A donor with no path sees the case record instead and can still give. See [03-trust-model.md](03-trust-model.md).

## 2. A donor gives directly

1. The donor opens a Live cause and chooses to give.
2. Wasl shows the presenter's checked payment details: the account title, and the bank account or wallet number.
3. The donor pays from their own bank or wallet app. Wasl takes no part in the transfer.
4. The donor comes back and records the gift: amount, date, method and transfer reference. The trust path they were shown is stored with it. This step is optional.
5. The presenter confirms the gift arrived. The cause total rises by the confirmed amount, and the donor gets an acknowledgement by email in their language.

If the presenter says a recorded gift did not arrive, it is marked disputed and an admin can look at it.

## 3. A presenter submits a cause

1. The presenter signs up, verifies email and phone, and names who introduced them.
2. They fill in the cause form in English, Urdu or both. They record the beneficiary and upload identity and consent evidence.
3. They add how donors will pay them: a bank account or wallet in their own name, with proof of the account title.
4. Submission puts the cause in the verifier queue for the baseline checks. The presenter sees its status.
5. The verifier approves, rejects, or asks for changes with a written reason.
6. On approval the cause goes Live and its payment details become visible. The presenter invites people who know them to add a trust link or endorse the cause, and shares the cause link.

**Assisted submission.** For a presenter who is not comfortable with forms, an admin enters steps 2 to 4 on their behalf. The cause records who entered it, and the presenter confirms it before review.

## 4. A presenter accounts for the money

1. Gifts arrive in the presenter's own account. The presenter confirms each recorded gift, and adds any that arrived without being recorded.
2. While the cause is Live and holds confirmed gifts, a proof-of-use update is due at least every 30 days (assumed), and a final one within 30 days of closing or reaching the goal.
3. The update shows what was paid, with receipts or photos. When the presenter is not the beneficiary, it must show the money reaching the beneficiary.
4. A missed update hides the payment details, flags the cause for review and shows on the presenter's history.
5. Donors who recorded a gift are notified of each update.
