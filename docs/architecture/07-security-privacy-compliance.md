# Security, privacy and compliance

Wasl holds identity documents, medical evidence, presenters' payment details and a social graph, so it is designed as a system handling special-category personal data from the start. Which laws apply depends on the target country and still needs legal review.

## Security

- Passwords hashed with Argon2id; two-factor sign-in mandatory for verifiers and admins
- Role checks on every API route, plus ownership checks so a presenter only ever reads their own causes and documents
- Evidence files in a private bucket, encrypted at rest, served only by signed URLs that expire in minutes; every view is written to the audit log
- Uploads limited by type and size and virus-scanned before a verifier can open them
- Rate limits on sign-in, sign-up, recording gifts, payment-detail lookups, reporting and trust lookups
- Secrets only in the host's secret store, never in the repository
- No card data, bank credentials or payment tokens are ever collected: Wasl handles no payments
- Payment details are editable only by the presenter, every change returns them to review and is logged, and they are served only for Live causes
- Append-only audit log, enforced by database permissions
- Dependency and secret scanning in CI

## Privacy

- Collect only what a check needs, and show verifiers only the documents for causes assigned to them
- Retention: evidence documents deleted a fixed period after a cause closes; gift records kept for the legally required term
- Donors can give anonymously to the public while Wasl still holds the record
- Data export and deletion requests handled through an admin workflow
- Beneficiaries, especially children and patients, are not identifiable in public content without recorded consent
- Published case documents are redacted of personal identifiers before anyone outside the review team can see them
- Identity documents are never published; payment details are shown only on Live causes and are removed when a cause closes

### Trust graph

- A trust link is personal data about two people. It is shown only to the person trusted and to people who trust its author, never publicly
- The person trusted is told about each new link and can remove it
- Path queries run on the server and return only what the viewer may see; no endpoint returns the wider graph
- Path and network lookups are rate-limited to stop the social graph being scraped
- Share previews never include trust paths
- Closing an account removes its links in both directions

## Compliance to confirm with counsel

None of these is settled. Each is tracked in [open questions](../open-questions.md).

- Data protection: UK GDPR if operated from or serving the UK; the applicable local law in the target country
- Fundraising and charity regulation, including whether Wasl must itself be a registered charity or work under one
- Whether a platform that only publishes payment details and records reported gifts is outside payment-services and anti-money-laundering rules
- Tax treatment: Wasl sends acknowledgements, not tax receipts
