# Wasl

Wasl (وصل, "connection") is a web platform where donors give to causes they can trace a line of trust to. Its core is a trust graph: people say who they trust, and a donor sees how they are connected to whoever presents a cause.

**No money flows through Wasl.** Donors give directly to the presenter, outside Wasl. Wasl never processes, holds or routes money, and nothing may be built that does.

Stack: Next.js (TypeScript) frontend, FastAPI (Python) backend, PostgreSQL. Languages: English and Urdu, right-to-left from day one.

## The docs are the source of truth

Everything about what Wasl is, how it is built and where the work stands lives in `docs/`. Do not rely on memory of earlier sessions or on chat history. If the docs and the code disagree, stop and resolve it: fix whichever is wrong and say which one you changed.

## Start of every session

1. Read `docs/development/STATUS.md`. It says which module is active, what was done last and what comes next.
2. Read the active module file it points to in `docs/development/modules/`.
3. Read only the design docs that module lists under "Read first". Do not load all of `docs/` by default.
4. Check `docs/open-questions.md` for anything that blocks the next task. Do not build past a blocker; ask.

## End of every session, and after each finished task

1. Tick the finished tasks in the module file and add anything discovered to its Notes.
2. Update `docs/development/STATUS.md`: last done, next up, blockers.
3. Add an entry to `docs/development/session-log.md`.
4. If a design decision was made or changed, record it in `docs/decisions.md` and update the design doc it affects in the same commit.
5. Commit. Docs and the code they describe change in the same commit.

## Doc map

| Path | Holds |
| --- | --- |
| `docs/README.md` | Index of all docs and the rules for editing them |
| `docs/product/` | What Wasl is: overview and scope, flows, trust model, seeding plan |
| `docs/architecture/` | How it is built: system, data model, API, languages, repo and tooling, giving without handling money, security and compliance |
| `docs/design/README.md` | Link to the UI design canvas and the inventory of screens |
| `docs/design/design-language.md` | The design language every screen follows: tokens, glass, components, motion, graph requirements |
| `docs/decisions.md` | Dated log of decisions and the assumptions still standing |
| `docs/open-questions.md` | Unanswered questions and which module each one blocks |
| `docs/development/STATUS.md` | Where the work stands right now |
| `docs/development/roadmap.md` | The modules in build order with their status |
| `docs/development/modules/` | One file per module: goal, tasks, acceptance, notes |
| `docs/development/session-log.md` | Append-only record of each working session |
| `docs/development/README.md` | The development process in full |

## Rules

- **Terminology.** The person who puts a cause on Wasl is the **presenter**. The person in need is the **beneficiary**. They are often different people. Use these words in code, routes and docs.
- **Scope.** Build only what the active module lists. New ideas go into `docs/open-questions.md` or the roadmap, not into the code.
- **Assumptions.** Values marked "assumed" in the docs (three-link depth, 30-day deadlines and so on) go in configuration, not in constants scattered through the code.
- **No money through Wasl.** No payment provider, checkout, balance, payout, refund or fee. Wasl shows the presenter's checked payment details and records gifts that donors report and presenters confirm. If a task seems to need a payment, stop: it conflicts with decision D-013. See `docs/architecture/06-giving.md`.
- **Amounts.** Integer minor units plus a currency code. The audit log is append-only.
- **Privacy.** Trust links are never public. Identity documents are never published. Payment details show only on Live causes. No endpoint returns the wider graph.
- **Design.** Every screen follows `docs/design/design-language.md`. Use its tokens, never raw colours.
- **Graphs are real graphs.** Built from API data with a computed layout, interactive. Never a static or hand-placed drawing.
- **Both languages.** Every user-facing string exists in English and Urdu. Use logical CSS properties, never left or right.
- **Tests.** A task is not done until its tests pass and CI is green.
- **No secrets in the repository.**
