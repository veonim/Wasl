# Open questions

Questions nobody has answered yet. Each says what it blocks. A module must not be built past a question marked **Blocks**; a question marked **Shapes** has an assumed default in [decisions.md](decisions.md) and can be built against that default.

When a question is answered: remove it from here, log the answer in [decisions.md](decisions.md), and update the design docs it touches.

## Business and legal

| ID | Question | Effect |
| --- | --- | --- |
| Q-01 | **Target country.** Where are the causes and where are the donors? Urdu suggests Pakistan, the diaspora, or both. This drives the payment provider, currency, hosting region and applicable law. | Blocks M4 (real provider), M6 |
| Q-02 | **Payment provider.** Which provider, once the country is known? Cards only, or local wallets and bank transfer too? | Blocks M4 (real provider) |
| Q-03 | **Custody of funds.** Does Wasl hold donations and pay out, or do funds go straight to the presenter? Under what legal entity? | Blocks M4 (real provider), M5 |
| Q-04 | **Who verifies.** In-house staff, partner NGOs, or volunteers? What is the expected turnaround for a baseline check? | Shapes M3 |
| Q-05 | **Cause types.** Registered organisations only, or individuals too? Individual appeals carry much higher fraud risk and checking cost. | Shapes M2 |
| Q-06 | **Revenue.** No platform fee is assumed. Is the model donor tips, a percentage, grants, or something else? | Shapes M4 |
| Q-07 | **Zakat.** Should zakat-eligible causes be labelled and their funds kept separate from the first release? | Shapes M2, M4 |
| Q-08 | **Thresholds.** The goal amount that triggers a second verifier, the proof-of-use deadline, the verification lifetime, the report count that pauses a cause. | Shapes M3, M5 |
| Q-09 | **Guest donations.** Allowed as assumed, or is an account required for anti-fraud reasons? | Shapes M4 |
| Q-10 | **Brand.** Is there an existing visual identity, or does design start from scratch? | Shapes M1 |
| Q-22 | **Legal review.** Data protection law, charity and fundraising regulation, anti-money-laundering duties and tax receipts for the chosen country. | Blocks M6 |

## Trust graph

| ID | Question | Effect |
| --- | --- | --- |
| Q-11 | **Depth and levels.** Three links and three trust levels are assumed. Are those right? | Shapes M3 |
| Q-12 | **Alongside checks or alone.** The design keeps staff identity and bank checks under the graph. Should the graph stand alone, or should a cause also need a minimum number of by-name vouches to go Live? | Blocks M3 |
| Q-13 | **How first users connect.** By invitation only, or also by matching phone contacts? | Shapes M3 |
| Q-14 | **Visibility.** Links are assumed visible only along the graph. Should they be more open, and can someone refuse to be vouched for? | Blocks M3 |
| Q-15 | **Accountability.** When a vouched cause proves fraudulent, is notifying the voucher's connections enough, or should the voucher lose the ability to vouch? | Shapes M3, M5 |

## Case record

| ID | Question | Effect |
| --- | --- | --- |
| Q-16 | **Published documents.** Who redacts personal details before a document is shown, the presenter or a reviewer? Must a reviewer check a document before it can be published? | Shapes M2 |
| Q-17 | **Presenter history.** Does history cover only cases run on Wasl, or can a presenter add earlier work from elsewhere, marked as unverified? | Shapes M2 |

## Seeding

| ID | Question | Effect |
| --- | --- | --- |
| Q-18 | Which community goes first? | Blocks pilot (M6) |
| Q-19 | Who are the first connectors, by name, and who approaches them? | Blocks pilot (M6) |
| Q-20 | Who does assisted onboarding during the pilot, and for how many cases a week? | Blocks pilot (M6) |
| Q-21 | Is submission invitation-only at launch, and are connectors unpaid, as proposed? | Shapes M2 |
