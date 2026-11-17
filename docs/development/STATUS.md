# Status

**Last updated:** 2026-11-17

## Where we are

| | |
| --- | --- |
| Phase | Design drafted. No application code exists. |
| Core rule | No money flows through Wasl (D-013). Donors give directly to presenters. |
| Active module | [M1 Foundation](modules/M1-foundation.md), not started |
| Next task | `M1-T01`: repository scaffold |
| Repository contains | `CLAUDE.md`, `README.md`, `docs/` only |

## Last done

- Design written and split into `docs/product/` and `docs/architecture/`.
- Decisions and standing assumptions logged in [decisions.md](../decisions.md).
- Development process, roadmap and module task lists created.
- All MVP screens drawn on the design canvas in the SUMMIT style. Inventory in [design/README.md](../design/README.md); design language in [design/design-language.md](../design/design-language.md).
- Graphs must be real, data-driven graphs (D-012).
- **Core design change (D-013): no money flows through Wasl.** The payment provider, checkout, ledger, payouts and refunds were removed from every doc. Giving is now direct to the presenter, with checked payment details, gifts recorded by donors and confirmed by presenters. Modules M4 and M5 were rewritten as Giving and Reporting and administration. The affected screens were redrawn.

## Next up

1. Product owner reviews the design docs and the UI screens. All are first drafts and have not been reviewed or checked as rendered.
2. A native reader checks the Urdu copy on the three Urdu screens.
3. Start M1 at `M1-T01`. M1, M2, M4 and M5 need no open question answered.

## Blockers

| Module | Blocked by |
| --- | --- |
| M3 Trust graph and baseline checks | Q-12 (graph alongside checks or alone), Q-14 (link visibility) |
| M6 Launch readiness | Q-18 to Q-20 (pilot community and connectors), Q-22 (legal review) |

M4 and M5 are no longer blocked: with no money through Wasl there is no payment provider or custody decision to wait for.

See [open questions](../open-questions.md).

## Known broken or half-finished

Nothing.
