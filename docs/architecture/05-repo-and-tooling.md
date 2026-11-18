# Repository, tooling and deployment

One repository holds both services, so a contract change and its frontend update land in the same pull request.

## Layout

This is the target layout. What exists today is listed in [STATUS](../development/STATUS.md).

```text
wasl/
  CLAUDE.md              anchor for AI-assisted sessions
  README.md
  apps/
    web/                 Next.js app
      src/app/[locale]/  routes: public, donor, presenter, verifier, admin
      src/components/
      src/lib/api/       client generated from OpenAPI
      messages/          en.json, ur.json
    api/                 FastAPI service
      app/
        core/            config, security, database, errors
        modules/         accounts, causes, trust, verification,
                         giving, admin
        providers/       storage, email, sms (with fakes)
        worker/          background jobs
      migrations/        Alembic
      tests/
  docs/                  source of truth: product, architecture, development
  infra/                 config for local services (storage keys)
  stencil/               blank copy of the docs structure for other projects
  docker-compose.yml     postgres, redis, object storage, mail catcher
  .env.example           local-only settings for docker-compose.yml
  .editorconfig
  .github/workflows/     CI
```

## Tooling

| Concern | Choice |
| --- | --- |
| Python tooling | uv, Ruff, mypy, pytest with a real PostgreSQL in CI |
| Frontend tooling | pnpm, ESLint, Prettier, Vitest, Playwright for end-to-end tests in both locales |
| Local development | `docker compose up` for dependencies: PostgreSQL 16, Redis, SeaweedFS as the S3-compatible store, Mailpit as the mail catcher. Fake storage, email and SMS providers in tests, so no external accounts are needed |
| CI | Lint, type-check, tests, OpenAPI client drift check, dependency and secret scan on every pull request |

## Environments and operations

| Concern | Choice |
| --- | --- |
| Environments | Local, staging, production |
| Hosting | Containers for API and worker, managed PostgreSQL and Redis, managed Next.js hosting or a third container. Vendor and region follow the target-country decision because of data residency. |
| Observability | Structured JSON logs with request IDs, error tracking, uptime checks, alerts on failed jobs and on cause totals that disagree with their gift rows |
| Backups | Daily database backups with point-in-time recovery, and a tested restore |
| Secrets | Host secret store only; never in the repository |
