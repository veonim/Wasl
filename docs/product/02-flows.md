# Key flows

Four flows carry the MVP. Each one ends in a record the others can rely on.

## 1. A donor checks trust

1. Hamza presents a cause. Bilal, who knows him, sets his trust in Hamza to *would vouch by name*.
2. Ayesha, who trusts Bilal but has never met Hamza, opens the cause.
3. The API searches for paths from Ayesha to Hamza, up to three links, and returns only links Ayesha is entitled to see.
4. The trust panel shows "You trust Bilal. Bilal would vouch for Hamza." and draws the path as a graph.
5. Ayesha can ask Bilal directly outside Wasl, then donates or not. Her donation records the path it came through.

A donor with no path sees the case record instead and can still donate. See [03-trust-model.md](03-trust-model.md).

## 2. A donor gives

1. The donor opens a Live cause and picks an amount.
2. The frontend asks the API for a donation intent. The API creates a pending donation and a checkout session with the payment provider.
3. The donor pays on the provider's hosted page. Card details never touch Wasl.
4. The provider calls the Wasl webhook. The API verifies the signature, marks the donation paid, writes ledger entries and updates the cause total.
5. The donor gets a receipt by email in their chosen language.

## 3. A presenter submits a cause

1. The presenter signs up, verifies email and phone, and names who introduced them.
2. They fill in the cause form in English, Urdu or both. They record the beneficiary and upload identity, bank and consent evidence.
3. Submission puts the cause in the verifier queue for the baseline checks. The presenter sees its status.
4. The verifier approves, rejects, or asks for changes with a written reason.
5. On approval the cause goes Live. The presenter invites people who know them to add a trust link or endorse the cause, and shares the cause link.

**Assisted submission.** For a presenter who is not comfortable with forms, an admin enters steps 2 and 3 on their behalf. The cause records who entered it, and the presenter confirms it before review.

## 4. Funds are released and reported

1. The presenter requests a disbursement of some or all of the raised amount.
2. An admin approves it. The payout goes to the verified bank account.
3. The presenter has 30 days (assumed) to post a proof-of-use update with receipts or photos. When the presenter is not the beneficiary, the update must show the money reaching the beneficiary.
4. A missed update blocks further disbursements and flags the cause for review.
5. Donors to the cause are notified of each update.
