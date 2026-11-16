# M1 Foundation

**Status:** Not started
**Depends on:** nothing
**Blocked by:** nothing

## Goal

A person can sign up, verify, sign in and switch between English and Urdu on a running app, and every later module has a tested base to build on.

## Read first

- [System architecture](../../architecture/01-system.md)
- [Repository, tooling and deployment](../../architecture/05-repo-and-tooling.md)
- [English and Urdu](../../architecture/04-languages.md)
- [Data model](../../architecture/02-data-model.md), Accounts section
- [Security](../../architecture/07-security-privacy-compliance.md), Security section

## Tasks

### Repository

- [ ] `M1-T01` Scaffold the repository: `apps/web`, `apps/api`, root `.gitignore`, `.editorconfig`, and `docker-compose.yml` with PostgreSQL, Redis, object storage and a mail catcher
- [ ] `M1-T02` CI workflow: lint, type-check and tests for both apps on every pull request, plus dependency and secret scanning

### API

- [ ] `M1-T03` FastAPI skeleton: settings from environment, health endpoint, shared error shape with code and message key, request IDs, structured logging
- [ ] `M1-T04` Database: async SQLAlchemy session, Alembic set up, first migration, pytest fixture running against a real PostgreSQL
- [ ] `M1-T05` Configuration for standing assumptions: one settings object holding path depth, deadlines and thresholds from [decisions.md](../../decisions.md)
- [ ] `M1-T06` `user` and `user_role` tables with migration, including `introduced by`
- [ ] `M1-T07` Provider interfaces with fakes for email and SMS
- [ ] `M1-T08` Register, login, refresh, logout: Argon2id hashing, access and rotating refresh tokens in HttpOnly cookies
- [ ] `M1-T09` Email and phone verification using the fake providers
- [ ] `M1-T10` Password reset
- [ ] `M1-T11` Role dependency for routes, and `GET` and `PATCH /me`
- [ ] `M1-T12` Rate limiting on sign-in and sign-up, backed by Redis

### Web

- [ ] `M1-T13` Next.js app with TypeScript, Tailwind and the base layout
- [ ] `M1-T14` next-intl with `/en` and `/ur` routes, language switcher, locale saved to cookie and profile
- [ ] `M1-T15` Right-to-left: `dir` on the root element, logical properties only, self-hosted Noto Nastaliq Urdu with its own type scale
- [ ] `M1-T16` API client generated from the OpenAPI schema, with a CI check that fails when it drifts
- [ ] `M1-T17` Sign-up, sign-in, verification and password-reset pages in both languages
- [ ] `M1-T18` Signed-in shell: header, account menu, placeholder home page

### Tests

- [ ] `M1-T19` Playwright end-to-end test: sign up, verify, sign in, switch language, sign out, in both locales

## Acceptance

- [ ] `docker compose up` plus two start commands brings up a working app from a fresh clone, as documented in the root README
- [ ] A new user can sign up, verify email and phone, sign in and sign out
- [ ] Switching to Urdu flips the whole layout right-to-left with Nastaliq type, and the choice persists
- [ ] An unverified or signed-out user cannot reach a signed-in route
- [ ] CI is green and fails when the generated API client is out of date

## Notes

Nothing yet.
