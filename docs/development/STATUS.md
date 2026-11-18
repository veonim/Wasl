# Status

**Last updated:** 2026-11-18

## Where we are

| | |
| --- | --- |
| Phase | Building M1. Design drafted and not yet reviewed. |
| Core rule | No money flows through Wasl (D-013). Donors give directly to presenters. |
| Active module | [M1 Foundation](modules/M1-foundation.md), in progress (1 of 20 tasks) |
| Next task | `M1-T02`: CI workflow |
| Repository contains | `CLAUDE.md`, `README.md`, `docs/`, `stencil/`, `docker-compose.yml` with local services, `infra/`, and placeholder `apps/api` and `apps/web` folders. No application code yet. |

## Last done

- Design written and split into `docs/product/` and `docs/architecture/`.
- Decisions and standing assumptions logged in [decisions.md](../decisions.md).
- Development process, roadmap and module task lists created.
- All MVP screens drawn on the design canvas in the SUMMIT style. Inventory in [design/README.md](../design/README.md); design language in [design/design-language.md](../design/design-language.md).
- Graphs must be real, data-driven graphs (D-012).
- **Core design change (D-013): no money flows through Wasl.** The payment provider, checkout, ledger, payouts and refunds were removed from every doc. Giving is now direct to the presenter, with checked payment details, gifts recorded by donors and confirmed by presenters. Modules M4 and M5 were rewritten as Giving and Reporting and administration. The affected screens were redrawn.
- Reusable documentation stencil added in `stencil/`.
- `M1-T01` done: repository scaffold with `.gitignore`, `.editorconfig`, `.env.example`, and `docker-compose.yml` running PostgreSQL 16, Redis, SeaweedFS and Mailpit.

## Next up

1. `M1-T02`: CI workflow. Note that it has nothing to lint or test until `M1-T03` and `M1-T13` create the apps, so it can be built alongside them.
2. `M1-T03`: FastAPI skeleton.
3. Product owner reviews the design docs and the UI screens. Both are first drafts.

## Blockers

| Module | Blocked by |
| --- | --- |
| M3 Trust graph and baseline checks | Q-12 (graph alongside checks or alone), Q-14 (link visibility) |
| M6 Launch readiness | Q-18 to Q-20 (pilot community and connectors), Q-22 (legal review) |

M4 and M5 are no longer blocked: with no money through Wasl there is no payment provider or custody decision to wait for.

See [open questions](../open-questions.md).

## Known broken or half-finished

- The local services in `docker-compose.yml` have been validated but not yet started; see the M1 notes.
