# M6 Launch readiness

**Status:** Not started
**Depends on:** M5
**Blocked by:** Q-18, Q-19, Q-20 (pilot community, connectors, onboarding staff), Q-22 (legal review). Also needs Q-01 for hosting region.

## Goal

Wasl is safe to put in front of real donors and real cases, and a pilot runs in one community.

## Read first

- [Security, privacy and compliance](../../architecture/07-security-privacy-compliance.md)
- [Repository, tooling and deployment](../../architecture/05-repo-and-tooling.md), environments and operations
- [Seeding](../../product/04-seeding.md)

## Tasks

### Security and privacy

- [ ] `M6-T01` Security review against the controls in the security doc, with findings fixed or logged
- [ ] `M6-T02` Check every endpoint for role and ownership enforcement; specific test that no endpoint leaks trust links
- [ ] `M6-T03` Retention jobs: delete evidence documents after the retention period
- [ ] `M6-T04` Legal pages in both languages: terms, privacy notice, how trust links are used and shown

### Quality

- [ ] `M6-T05` Accessibility pass in both languages, including keyboard use and the graph's text equivalent
- [ ] `M6-T06` Load test of the API, including path search on a large synthetic graph
- [ ] `M6-T07` Review of all Urdu text by a native reader

### Operations

- [ ] `M6-T08` Staging and production environments in the chosen region
- [ ] `M6-T09` Error tracking, uptime checks, alerts on webhook failures and ledger mismatches
- [ ] `M6-T10` Backups with point-in-time recovery, and a restore drill
- [ ] `M6-T11` Runbook: deploy, roll back, handle a fraud report, handle a payment incident

### Pilot

- [ ] `M6-T12` Onboard the first hand-picked cases by assisted submission
- [ ] `M6-T13` Onboard the first connectors and record their introductions
- [ ] `M6-T14` Pilot review: what donors used, where presenters struggled, what to change

## Acceptance

- [ ] No open high-severity security finding
- [ ] A restore from backup has been done and timed
- [ ] Legal review is complete for the launch country
- [ ] Both languages pass the accessibility checks
- [ ] Real causes are live, entered through assisted submission, with at least one donation made through a trust path

## Notes

Nothing yet.
