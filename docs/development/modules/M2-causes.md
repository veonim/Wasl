# M2 Causes

**Status:** Not started
**Depends on:** M1
**Blocked by:** nothing. Shaped by Q-05, Q-07, Q-16, Q-17, Q-21; build against the defaults in [decisions.md](../../decisions.md).

## Goal

A presenter, or staff on their behalf, can submit a cause with evidence, and anyone can browse causes and read the full case record. Causes are created directly in the Live state by seed data or an admin switch until M3 adds review.

## Read first

- [Overview](../../product/01-overview.md)
- [Flows](../../product/02-flows.md), flow 3
- [Trust model](../../product/03-trust-model.md), the case record section
- [Seeding](../../product/04-seeding.md), what the product must support
- [Data model](../../architecture/02-data-model.md), Causes section
- [API](../../architecture/03-api.md)

## Tasks

### API

- [ ] `M2-T01` `organisation`, `cause`, `cause_translation` tables with migrations, including beneficiary fields and `entered by`
- [ ] `M2-T02` Storage provider interface with a fake and an S3-compatible implementation; signed upload and download URLs
- [ ] `M2-T03` `cause_document` table; upload flow with type, size and checksum checks; visibility and reviewer-checked flags
- [ ] `M2-T04` Presenter endpoints: create draft, edit, add documents, submit
- [ ] `M2-T05` Beneficiary consent: required document when presenter and beneficiary differ
- [ ] `M2-T06` Assisted submission: admin creates a cause on a presenter's behalf and hands it over for confirmation
- [ ] `M2-T07` Introduced by: captured at presenter sign-up, confirmed by the introducer
- [ ] `M2-T08` Public listing with full-text search in both languages (simple configuration plus trigram), category and location filters, cursor pagination
- [ ] `M2-T09` Public cause detail, published documents endpoint, and presenter history computed from existing tables
- [ ] `M2-T10` `cause_update` and `report` tables; public reporting endpoint with rate limit
- [ ] `M2-T11` Seed script with invented causes, presenters and documents in both languages

### Web

- [ ] `M2-T12` Submission form: story in one or both languages, goal, use-of-funds breakdown, beneficiary, uploads, save as draft
- [ ] `M2-T13` Presenter dashboard with a status tracker per cause
- [ ] `M2-T14` Admin assisted-submission screen
- [ ] `M2-T15` Public listing page with search and filters
- [ ] `M2-T16` Cause page: story, goal and progress, the case record (documents, presenter history, updates, baseline checks placeholder, vouch count placeholder), language fallback note
- [ ] `M2-T17` Share previews: Open Graph tags and generated preview image per locale

### Tests

- [ ] `M2-T18` End-to-end: presenter submits a cause with a beneficiary and documents; a guest finds it in search and reads the case record, in both locales

## Acceptance

- [ ] A presenter can create, save, edit and submit a cause in English, Urdu or both
- [ ] A cause where presenter and beneficiary differ cannot be submitted without a consent document
- [ ] An admin can enter a cause for a presenter, and the cause shows who entered it
- [ ] A guest can search, filter and open a cause and see every part of the case record
- [ ] Private documents are never reachable by a guest or by another presenter
- [ ] A cause link pasted into a chat app shows a preview with title, goal and progress
- [ ] Urdu search finds Urdu causes

## Notes

Nothing yet.
