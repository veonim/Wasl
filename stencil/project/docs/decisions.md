# Decisions

A dated log of what has been decided, and a list of the assumptions that stand until someone confirms or changes them.

## How to use this file

- Add a decision when a design choice is made or changed. Newest at the bottom, numbered `D-NNN`.
- Status is **Decided** (confirmed by the product owner) or **Proposed** (chosen in the design, not yet reviewed).
- When a decision replaces an earlier one, mark the earlier one "Superseded by D-NNN". Do not delete it.
- When an assumption is confirmed or changed, move it from the assumptions table into the log.

## Log

| ID | Date | Decision | Status | Affects |
| --- | --- | --- | --- | --- |
| D-001 | [YYYY-MM-DD] | [What was decided, in one or two sentences.] | [Decided / Proposed] | [Link to the doc it changes] |
| D-002 | [YYYY-MM-DD] | The docs in this repository are the source of truth. `CLAUDE.md` is the anchor. Development is tracked module by module in `docs/development/`. | Decided | [docs index](README.md) |

## Standing assumptions

Each of these was chosen to keep the design moving. None is confirmed. Each must be a configuration value or an easily changed rule, not a constant spread through the code.

| ID | Assumption | Related question |
| --- | --- | --- |
| A-01 | [The value or rule being assumed.] | Q-[NN] |
