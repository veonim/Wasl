# [PROJECT NAME] documentation

These files are the source of truth for [PROJECT NAME]. Design, decisions and progress all live here, so that work can resume at any time without relying on anyone's memory or on chat history.

## Index

### Product: what it is

| File | Holds |
| --- | --- |
| [product/01-overview.md](product/01-overview.md) | Summary, users and roles, scope, later, non-goals |
| [product/02-flows.md](product/02-flows.md) | The key flows, step by step |

### Architecture: how it is built

| File | Holds |
| --- | --- |
| [architecture/01-system.md](architecture/01-system.md) | Components and the design choices behind them |
| [architecture/02-data-model.md](architecture/02-data-model.md) | Tables or entities and their rules |
| [architecture/03-api.md](architecture/03-api.md) | Endpoints by area |

### Design: how it looks

| File | Holds |
| --- | --- |
| [design/README.md](design/README.md) | Link to the design canvas and the inventory of screens drawn |
| [design/design-language.md](design/design-language.md) | Tokens, components, states, motion, accessibility |

### Decisions and questions

| File | Holds |
| --- | --- |
| [decisions.md](decisions.md) | Dated decision log, and the assumptions still standing |
| [open-questions.md](open-questions.md) | Unanswered questions and what each one blocks |

### Development: where the work stands

| File | Holds |
| --- | --- |
| [development/README.md](development/README.md) | The development process |
| [development/STATUS.md](development/STATUS.md) | Current state: active module, last done, next up |
| [development/roadmap.md](development/roadmap.md) | Modules in build order with status |
| [development/modules/](development/modules/) | One file per module with tasks and acceptance criteria |
| [development/session-log.md](development/session-log.md) | Record of each working session |

## Rules for editing these docs

1. **One fact, one place.** Each fact lives in one file. Other files link to it instead of repeating it.
2. **Docs change with the code.** A change to behaviour, schema or API updates its doc in the same commit.
3. **Decisions are logged.** A design decision gets an entry in `decisions.md`, and the design doc is updated to match. Do not leave the reasoning only in a commit message.
4. **Answered questions move.** When an open question is answered, remove it from `open-questions.md`, log the answer in `decisions.md` and update the design docs.
5. **Assumptions are marked.** A value nobody has confirmed is written with "(assumed)" and listed in `decisions.md` under standing assumptions.
6. **Progress is recorded where it happens.** Task ticks go in the module file, the current position in `STATUS.md`, the narrative in `session-log.md`.
