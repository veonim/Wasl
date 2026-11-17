# Project documentation stencil

A blank copy of the documentation and development-tracking structure used by Wasl, for starting any new project. Copy the `project/` folder into a new repository's root, then fill in the placeholders.

The aim: anyone, human or AI, can open the repository cold and know within two minutes what the project is, what has been built, what is next and what is in the way, without relying on chat history or memory.

## How to use it

1. Copy everything inside `project/` to the root of the new repository.
2. Replace every `[PLACEHOLDER]`. Search for `[` to find them. Delete the `> Guidance:` lines as you fill each section.
3. Fill in this order:
    1. `CLAUDE.md`: name, one-paragraph description, core rules, stack
    2. `docs/product/01-overview.md`: the problem, users, scope
    3. `docs/decisions.md`: the decisions already made, and the assumptions you are working on
    4. `docs/open-questions.md`: everything still unknown, each marked Blocks or Shapes
    5. `docs/architecture/`: system, data model, API
    6. `docs/development/roadmap.md` and one file per module from `modules/_TEMPLATE.md`
    7. `docs/development/STATUS.md`: point at the first module and its first task
4. Add or remove product and architecture files to suit the project. Keep the numbering, and add each new file to `docs/README.md` and the doc map in `CLAUDE.md`.
5. Commit. From then on, follow the session routine in `CLAUDE.md`.

## What goes where

```text
CLAUDE.md                         anchor: what this is, core rules, session routine, doc map
README.md                         short public front page
docs/
  README.md                       index of every doc, and the rules for editing docs
  product/                        WHAT: problem, users, scope, flows, domain rules
    01-overview.md
    02-flows.md
  architecture/                   HOW: system, data, API, cross-cutting concerns
    01-system.md
    02-data-model.md
    03-api.md
  design/                         LOOK: canvas link, screen inventory, design language
    README.md
    design-language.md
  decisions.md                    dated decisions log + standing assumptions
  open-questions.md               unknowns, each saying what it blocks
  development/                    PROGRESS: where the work stands
    README.md                     the development process
    STATUS.md                     where we are right now
    roadmap.md                    modules in order with status
    session-log.md                append-only record of each session
    modules/
      _TEMPLATE.md                copy for each module: goal, tasks, acceptance, notes
```

## The four kinds of file

| Kind | Files | Changes when |
| --- | --- | --- |
| **Truth about the product** | `product/`, `architecture/`, `design/` | A design decision is made or changed |
| **Why it is that way** | `decisions.md` | Something is decided, or an assumption is confirmed |
| **What is unknown** | `open-questions.md` | A question is raised or answered |
| **Where the work stands** | `development/` | A task is finished, or a session ends |

## The rules that make it work

- **One fact, one place.** Other files link to it instead of repeating it.
- **Docs change with the code**, in the same commit.
- **Every decision is logged** in `decisions.md` with an ID (`D-001`), and the design doc is updated to match.
- **Every assumption is marked** "(assumed)" where it is used and listed in `decisions.md` with an ID (`A-01`) and the question that would settle it.
- **Every unknown is a numbered question** (`Q-01`) that says whether it **Blocks** a module or only **Shapes** it.
- **Work is tracked by module**, each with numbered tasks (`M1-T01`) and acceptance criteria. Commit messages carry the task ID.
- **Every session starts** by reading `STATUS.md` and **ends** by updating it and the session log.

## IDs at a glance

| Prefix | Meaning | Lives in |
| --- | --- | --- |
| `D-001` | Decision | `docs/decisions.md` |
| `A-01` | Standing assumption | `docs/decisions.md` |
| `Q-01` | Open question | `docs/open-questions.md` |
| `M1` | Module | `docs/development/modules/M1-*.md` |
| `M1-T01` | Task in a module | the module file |
