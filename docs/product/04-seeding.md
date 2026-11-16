# Seeding the platform

Wasl gets its first legitimate cases by recruiting the people cases already come to, not the people in need themselves. Each of these connectors brings several cases they can stand behind and a circle of donors who already trust them, so one connector seeds both sides.

## Who to recruit

A connector is someone who is already asked for help and already vets appeals informally.

| Connector | What they bring |
| --- | --- |
| Doctor or welfare officer at a charity hospital | Patients who cannot pay, with medical letters and cost estimates |
| Mosque or welfare committee member | Local families in hardship the committee already knows |
| School principal or teacher | Students behind on fees, with fee notices |
| Diaspora association organiser | Cases back home, and donors abroad who trust the organiser |
| Small registered charity or fee fund | A backlog of checked cases with documents, and little online reach |

## The order to do it in

1. **Start with the founders' own network.** Hand-pick 10 to 20 cases that you or people you trust can personally stand behind. Wasl staff do the onboarding for them: documents, write-up, translation. The first cases must be beyond doubt, because one early fraud damages a trust platform more than slow growth does.
2. **Recruit 5 to 10 connectors in one community.** One city or one diaspora community, not a whole country. The graph only works where it is dense: a few hundred people who know each other are worth more than thousands of strangers.
3. **Add two or three vetted sources.** Hospital welfare departments, fee funds and small charities fill the case record and presenter history from the first week.
4. **Replace the forwarded appeal.** People already pass appeals around as screenshots on WhatsApp, and every recipient asks whether it is real. A Wasl link shows the documents and, for a signed-in recipient, "you trust X, and X vouches for this". The pitch to a presenter is that their case is believed without answering the same question fifty times.
5. **Widen one community at a time.** Open the next community only when the first has connectors, repeat presenters and donors arriving through trust paths.

## What makes presenting a case worth it

- No platform fee
- Fast payout to a verified account
- Onboarding and support in Urdu, including over WhatsApp
- Help with the write-up and documents, so a connector spends minutes, not hours
- A track record that builds with every finished case and makes the next one easier to fund

## What the product must support

Seeding this way shapes the design in four places.

| Need | Design change | Specified in |
| --- | --- | --- |
| The presenter is often not the person in need | A cause records presenter and beneficiary separately, with the beneficiary's consent on file. Trust paths lead to the presenter. | [03-trust-model.md](03-trust-model.md), [data model](../architecture/02-data-model.md) |
| Connectors and beneficiaries may not be comfortable with forms | Assisted submission: Wasl staff fill in the case on someone's behalf, and the cause shows who entered it | [02-flows.md](02-flows.md), [API](../architecture/03-api.md) |
| A new presenter needs a first link | Introduced by: each new presenter names who brought them in. Once confirmed, it is their first trust link, and it tells Wasl which connectors bring good cases. | [03-trust-model.md](03-trust-model.md) |
| Cases must travel through WhatsApp | Shareable cause link with a preview image and summary in the sharer's language. Trust paths appear only after sign-in. | [system](../architecture/01-system.md) |

## What not to do

These are proposals, not yet confirmed. See [open questions](../open-questions.md).

- Do not open public self-service submission at launch. Unknown presenters with no introducer are the highest fraud risk and the hardest to check.
- Do not relax the baseline identity and bank checks to speed up onboarding.
- Do not pay connectors per case. Payment per case turns a vouch into a sale.
- Do not launch in several communities at once.
