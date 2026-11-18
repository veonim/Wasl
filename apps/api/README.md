# Wasl API

FastAPI service: auth, roles, the trust graph and path search, causes, payment details and the record of gifts, proof of use, and the audit log. It is the only component that touches the database or files. It never processes, holds or routes money (D-013).

**Status:** placeholder. The service is created in module M1:

| Task | Adds |
| --- | --- |
| `M1-T03` | FastAPI skeleton: settings, health endpoint, error shape, request IDs, logging |
| `M1-T04` | Database session, Alembic, first migration, test fixture against real PostgreSQL |
| `M1-T05` | Configuration for the standing assumptions |
| `M1-T06` to `M1-T12` | Accounts, auth, verification, roles, rate limiting |

Target layout, from [repository and tooling](../../docs/architecture/05-repo-and-tooling.md):

```text
apps/api/
  app/
    core/        config, security, database, errors
    modules/     accounts, causes, trust, verification, giving, admin
    providers/   storage, email, sms (with fakes)
    worker/      background jobs
  migrations/    Alembic
  tests/
```

Tooling: Python 3.12, uv, Ruff, mypy, pytest.
