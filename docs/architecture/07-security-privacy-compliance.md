# Security, privacy and compliance

Wasl holds identity documents, medical evidence, payment records and a social graph, so it is designed as a system handling special-category personal data from the start. Which laws apply depends on the target country and still needs legal review.

## Security

- Passwords hashed with Argon2id; two-factor sign-in mandatory for verifiers and admins
- Role checks on every API route, plus ownership checks so a presenter only ever reads their own causes and documents
- Evidence files in a private bucket, encrypted at rest, served only by signed URLs that expire in minutes; every view is written to the audit log
- Uploads limited by type and size and virus-scanned before a verifier can open them
- Rate limits on sign-in, sign-up, donation creation, reporting and trust lookups
- Webhook signatures verified; secrets only in the host's secret store, never in the repository
- Append-only audit log and ledger, enforced by database permissions
- Dependency and secret scanning in CI

## Privacy

- Collect only what a check needs, and show verifiers only the documents for causes assigned to them
- Retention: evidence documents deleted a fixed period after a cause closes; financial records kept for the legally required term
- Donors can give anonymously to the public while Wasl still holds the record
- Data export and deletion requests handled through an admin workflow
- Beneficiaries, especially children and patients, are not identifiable in public content without recorded consent
- Published case documents are redacted of personal identifiers before anyone outside the review team can see them
- Identity and bank documents are never published

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
- Anti-money-laundering and sanctions screening for presenters and large donations
- Tax receipts and Gift Aid or local equivalents
