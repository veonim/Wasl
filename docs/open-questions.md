# Open questions

Questions nobody has answered yet. Each says what it blocks. A module must not be built past a question marked **Blocks**; a question marked **Shapes** has an assumed default in [decisions.md](decisions.md) and can be built against that default.

When a question is answered: remove it from here, log the answer in [decisions.md](decisions.md), and update the design docs it touches.

Answered so far: Q-02 (payment provider) and Q-03 (custody of funds) were closed by D-013, no money flows through Wasl.

## Business and legal

| ID | Question | Effect |
| --- | --- | --- |
| Q-01 | **Target country.** Where are the causes and where are the donors? Urdu suggests Pakistan, the diaspora, or both. This drives which payment methods presenters can list, the currency, hosting region and applicable law. | Shapes M4; blocks M6 |
| Q-04 | **Who verifies.** In-house staff, partner NGOs, or volunteers? What is the expected turnaround for a baseline check? | Shapes M3 |
| Q-05 | **Cause types.** Registered organisations only, or individuals too? Individual appeals carry much higher fraud risk and checking cost. | Shapes M2 |
| Q-06 | **Revenue.** With no money through Wasl there is no fee on a gift. How is Wasl funded: grants, sponsors, separate voluntary support, or something else? | Shapes nothing in the MVP |
| Q-07 | **Zakat.** Should zakat-eligible causes be labelled, and should a donor be able to mark a gift as zakat? | Shapes M2, M4 |
| Q-08 | **Thresholds.** The goal amount that triggers a second verifier, the verification lifetime, the report count that pauses a cause. | Shapes M3, M5 |
| Q-09 | **Guests.** Can a guest see payment details and record a gift, as assumed, or is an account required? | Shapes M4 |
| Q-10 | **Logo and name mark.** The visual style is decided (D-011). Is there a logo, or should one be designed? | Shapes M1 |
| Q-22 | **Legal review.** Data protection law and charity or fundraising regulation for the chosen country, and confirmation that a platform which only publishes payment details is outside payment-services rules. | Blocks M6 |

## Giving without handling money

| ID | Question | Effect |
| --- | --- | --- |
| Q-23 | **Payment methods.** Which kinds can a presenter list: bank account, mobile wallets, international transfer for diaspora donors? | Shapes M4 |
| Q-24 | **Who sees payment details.** Anyone on a Live cause, as assumed, or only signed-in users? Public details are easier to give to and easier to scrape. | Shapes M4 |
| Q-25 | **What counts as raised.** Only gifts the presenter confirms are assumed to count. Should a donor be able to attach proof of transfer, and should staff ever confirm a gift? | Shapes M4 |
| Q-26 | **Proof-of-use timing.** With no payouts to hang a deadline on, the assumed rule is every 30 days while Live with confirmed gifts, and a final report within 30 days of closing. Is that right? | Shapes M5 |
| Q-27 | **Reaching the goal.** Payment details are assumed to hide automatically at the goal. Should a presenter be able to keep collecting? | Shapes M4 |
| Q-28 | **Disputes.** When a donor says they gave and the presenter says nothing arrived, what does Wasl do beyond recording it? | Shapes M4, M5 |

## Trust graph

| ID | Question | Effect |
| --- | --- | --- |
| Q-11 | **Depth and levels.** Three links and three trust levels are assumed. Are those right? | Shapes M3 |
| Q-12 | **Alongside checks or alone.** The design keeps staff checks of identity and payment details under the graph. Should the graph stand alone, or should a cause also need a minimum number of by-name vouches to go Live? | Blocks M3 |
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
