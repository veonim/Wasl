# M3 Trust graph and baseline checks

**Status:** Not started
**Depends on:** M2
**Blocked by:** Q-12 (graph alongside checks or alone), Q-14 (link visibility). Shaped by Q-04, Q-08, Q-11, Q-13, Q-15.

## Goal

A signed-in donor opening a cause sees how they are connected to its presenter, in words and as a graph. A cause reaches Live only through the baseline checks, and every status change is recorded.

This is the largest module. Part A (trust graph) and Part B (baseline checks) are independent and can be built in either order.

## Read first

- [Trust model](../../product/03-trust-model.md), all of it
- [Flows](../../product/02-flows.md), flows 1 and 3
- [Data model](../../architecture/02-data-model.md), Trust, Verification and Audit sections
- [API](../../architecture/03-api.md), trust rules
- [Security, privacy and compliance](../../architecture/07-security-privacy-compliance.md), trust graph section

## Tasks

### Part A: trust graph, API

- [ ] `M3-T01` `trust_link` table, indexed on both ends; set, change and withdraw a link at one of the configured levels; requires a verified phone
- [ ] `M3-T02` Top-level vouch waiting period for new accounts, from configuration
- [ ] `M3-T03` Notify the trusted person of a new link; let them remove it
- [ ] `M3-T04` `trust_invitation` table; invite by phone, email or user, with a daily cap
- [ ] `M3-T05` Introduced-by confirmation creates the presenter's first trust link
- [ ] `M3-T06` `cause_endorsement` table and endpoints
- [ ] `M3-T07` Path search: bidirectional breadth-first search to the configured depth, behind an interface, ranking paths by link levels and counting independent paths
- [ ] `M3-T08` Visibility rule inside the search: return only links whose author the viewer trusts, and links to the viewer
- [ ] `M3-T09` `GET /causes/{slug}/trust`: paths for a signed-in viewer, counts only for a guest
- [ ] `M3-T10` `GET /me/trust` and `GET /me/network`, paged by distance
- [ ] `M3-T11` Sort the cause listing by closeness in the viewer's graph
- [ ] `M3-T12` Rate limits on path and network lookups
- [ ] `M3-T13` Tests for path search on a synthetic graph: correctness, depth cap, visibility, and that a disconnected fake cluster yields no path

### Part A: trust graph, web

- [ ] `M3-T14` Trust panel on the cause page: paths in words, strongest first, with the no-path and guest states
- [ ] `M3-T15` Graph view of the paths with a graph library, expandable, mirrored in Urdu, with a plain-text equivalent
- [ ] `M3-T16` My network page
- [ ] `M3-T17` Trust controls: set a level on a person's profile, withdraw, invite, endorse a cause

### Part B: baseline checks, API

- [ ] `M3-T18` `audit_log` table, append-only by database permission, written on every staff action and status change
- [ ] `M3-T19` Cause lifecycle state machine matching the diagram in the trust model; remove the M2 shortcut that created causes as Live
- [ ] `M3-T20` `verification_review` table; verifier queue; approve, reject and request-changes with a written reason
- [ ] `M3-T21` Checklist per cause: identity, bank account, legal standing, beneficiary consent, optional need review that earns the Platform-checked badge
- [ ] `M3-T22` Two-person rule above the configured goal threshold; conflict-of-interest rule
- [ ] `M3-T23` Two-factor sign-in for verifiers and admins
- [ ] `M3-T24` Worker with Arq; expiry job that returns a cause to review after the configured lifetime or a key-fact edit
- [ ] `M3-T25` Reports: pause donations at the configured count or on a verifier report; admin decision to clear or close
- [ ] `M3-T26` Evidence views written to the audit log; virus scan before a verifier can open a file
- [ ] `M3-T27` Status emails to the presenter in their language

### Part B: baseline checks, web

- [ ] `M3-T28` Verifier queue and review screen with checklist and internal notes
- [ ] `M3-T29` Baseline checks shown on the cause page: which passed, the date, the reviewer's role
- [ ] `M3-T30` Presenter view of review status and requested changes

### Tests

- [ ] `M3-T31` End-to-end, flow 1: Ayesha trusts Bilal, Bilal vouches for Hamza, Ayesha sees the path on Hamza's cause; a stranger does not
- [ ] `M3-T32` End-to-end, review: submit, request changes, resubmit, approve, cause goes Live

## Acceptance

- [ ] A donor two links from a presenter sees the path in words and as a graph
- [ ] A donor with no path sees the no-path state and the case record
- [ ] A guest sees counts only, never names or links
- [ ] No API response exposes a link the viewer is not entitled to see
- [ ] Withdrawing a link removes the path at once
- [ ] A cause cannot reach Live without the required checks, and every transition appears in the audit log with a named actor
- [ ] A verifier cannot review a cause they present
- [ ] The graph view works right-to-left and has a text equivalent
- [ ] Path search on a synthetic graph of realistic size answers within an acceptable time, recorded in Notes

## Notes

Nothing yet.
