# Wasl

Wasl (وصل, "connection") is a bridge between donors and causes they can trust. Donors see how they are connected, through people they already trust, to the person presenting a cause. Donors with no connection decide on the case record: documents, case details and the presenter's history.

No money flows through Wasl. Donors give directly to the presenter; Wasl shows who to trust and how to pay them.

**Status:** design complete in draft, no code yet. See [`docs/development/STATUS.md`](docs/development/STATUS.md).

## Where to look

- [`docs/README.md`](docs/README.md): index of all documentation
- [`docs/product/01-overview.md`](docs/product/01-overview.md): what Wasl is and what the MVP includes
- [`docs/product/03-trust-model.md`](docs/product/03-trust-model.md): the trust graph and the case record
- [`docs/architecture/01-system.md`](docs/architecture/01-system.md): how it is built
- [`docs/development/roadmap.md`](docs/development/roadmap.md): what gets built, in what order
- [`CLAUDE.md`](CLAUDE.md): working rules for AI-assisted sessions
- [`stencil/`](stencil/README.md): a blank copy of this documentation and tracking structure, for starting other projects

## Stack

Next.js and TypeScript on the frontend, FastAPI and Python on the backend, PostgreSQL, Redis. English and Urdu with right-to-left layout.
