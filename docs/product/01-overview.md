# Overview

Wasl (وصل, "connection") is a web platform where donors give to causes they can trace a line of trust to. Its core is a trust graph: people say who they trust, and a donor sees how they are connected to whoever presents a cause.

## The problem

Donors cannot easily tell a real appeal from a fake one, and honest presenters have no credible way to prove themselves.

Wasl answers it the way people already do, by asking someone they trust. If a friend presents a case and you trust that friend, people who trust you can see that link and decide on the strength of it.

A donor with no connections can still see every cause and decide on a second layer, the case record: the case's documents, its details and the presenter's history of previous cases.

Under both layers sit baseline checks of identity and payment details, a record of gifts that presenters confirm, and required proof-of-use updates.

**No money flows through Wasl.** A donor gives directly to the presenter's own bank account or wallet. Wasl shows who to trust and how to pay them, and never processes, holds or routes money. See [giving](../architecture/06-giving.md). The full model is in [03-trust-model.md](03-trust-model.md).

## Users and roles

Four roles cover the MVP. One account can hold more than one role, except that a verifier can never review a cause they present. Adding trust links and endorsing causes is open to every signed-in user and needs no role.

The presenter is the person who puts a cause on Wasl. The beneficiary is the person in need. They are often different people.

| Role | What they do | Account needed |
| --- | --- | --- |
| Donor | Browse and search causes, see trust paths, give directly to the presenter, record the gift, follow updates | Optional for giving and recording a gift; required for trust paths and a giving history |
| Presenter | Submit a cause with evidence, answer reviewer questions, list how donors can pay them, confirm gifts received, post proof-of-use updates | Yes, with verified email and phone |
| Verifier | Run the baseline checks, approve, reject or request changes, re-review on a schedule | Yes, staff-issued, with two-factor sign-in |
| Admin | Manage users and verifiers, enter cases on a presenter's behalf, suspend and close causes, handle reports and disputed gifts, view the audit log | Yes, staff-issued, with two-factor sign-in |

## Scope

The MVP proves one loop end to end: a cause goes live, a donor sees why to trust it and gives directly, the presenter confirms and reports back.

### In the MVP

**Trust**

- Trust links between users at three levels, with invitations to connect
- Trust panel on every cause page: the viewer's paths to the presenter in words and as a graph
- My network page: the viewer's own graph, explorable
- Endorsing a specific cause
- Introduced by: each new presenter names who brought them in, which becomes their first trust link

**Causes**

- Public cause listing with search, category and location filters, sortable by closeness in the viewer's graph
- Cause detail page: story, goal and progress, published documents, presenter profile with history of previous cases, baseline checks, updates
- Presenter submission form with document upload and a status tracker
- Presenter and beneficiary recorded separately, with the beneficiary's consent on file
- Assisted submission: staff enter a case on a presenter's behalf
- Shareable cause links with a preview built for WhatsApp, in both languages

**Giving, with no money through Wasl**

- The presenter's checked payment details on every Live cause, with the account title
- Donors record a gift they made directly; presenters confirm it arrived
- Cause totals built from confirmed gifts only
- Email acknowledgements and a donor history page
- Proof-of-use updates that presenters must post on a schedule

**Staff**

- Verifier queue for baseline checks, with internal notes and approve, reject or request-changes actions
- Admin console: users, causes, reports, disputed gifts, payment-detail changes, audit log

**Languages**

- English and Urdu throughout, including emails

### Later

- Reminders for donors who want to give regularly
- Zakat and sadaqah labelling with eligibility rules per cause
- Organisation accounts with several team members
- Mobile apps, SMS and WhatsApp notifications
- Public impact reports
- Additional languages

### Non-goals

- Wasl does not process, hold or route money: no payment provider, no checkout, no balances, no payouts, no refunds, no fee on gifts
- Wasl does not run causes itself or deliver aid
- No peer-to-peer transfers between users
- No crypto payments
- No public trust score or ranking of people: trust is always shown relative to the viewer
- No general social network features: no feed, no messaging, no public friend lists
- No automated approval of causes: a person makes every baseline decision
