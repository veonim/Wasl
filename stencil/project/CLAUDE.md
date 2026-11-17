# [PROJECT NAME]

[One paragraph: what this project is, who it is for, and the one idea at its core.]

**[CORE RULE, if any.]** [A rule so fundamental that nothing may be built that breaks it. Delete this line if there is none.]

Stack: [frontend], [backend], [database]. Languages: [interface languages].

## The docs are the source of truth

Everything about what [PROJECT NAME] is, how it is built and where the work stands lives in `docs/`. Do not rely on memory of earlier sessions or on chat history. If the docs and the code disagree, stop and resolve it: fix whichever is wrong and say which one you changed.

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
| `docs/product/` | What [PROJECT NAME] is: overview and scope, flows[, other product docs] |
| `docs/architecture/` | How it is built: system, data model, API[, other architecture docs] |
| `docs/design/README.md` | Link to the design canvas and the inventory of screens |
| `docs/design/design-language.md` | The design language every screen follows |
| `docs/decisions.md` | Dated log of decisions and the assumptions still standing |
| `docs/open-questions.md` | Unanswered questions and which module each one blocks |
| `docs/development/STATUS.md` | Where the work stands right now |
| `docs/development/roadmap.md` | The modules in build order with their status |
| `docs/development/modules/` | One file per module: goal, tasks, acceptance, notes |
| `docs/development/session-log.md` | Append-only record of each working session |
| `docs/development/README.md` | The development process in full |

## Rules

> Guidance: keep each rule to one or two lines. These are the rules most likely to be broken by someone who has not read the docs.

- **Terminology.** [Key domain words and what they mean. Use these words in code, routes and docs.]
- **Scope.** Build only what the active module lists. New ideas go into `docs/open-questions.md` or the roadmap, not into the code.
- **Assumptions.** Values marked "assumed" in the docs go in configuration, not in constants scattered through the code.
- **[Core rule].** [Restate it, and what to do if a task seems to need breaking it. Link the doc that explains it.]
- **[Data rule].** [For example: how amounts, dates or IDs are stored; what is append-only.]
- **Privacy.** [What must never be public or leave the system.]
- **Design.** Every screen follows `docs/design/design-language.md`. Use its tokens, never raw values.
- **[Languages].** [For example: every user-facing string exists in every supported language.]
- **Tests.** A task is not done until its tests pass and CI is green.
- **No secrets in the repository.**
