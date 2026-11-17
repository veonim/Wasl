# Development process

Work is organised by module, not by sprint. A module is finished when its acceptance criteria pass, however long that takes. Modules are built in order because each depends on the one before.

The aim of this process is that anyone, human or AI, can open the repository cold and know within two minutes what is built, what is next and what is in the way.

## The four files that track progress

| File | Answers | Updated |
| --- | --- | --- |
| [STATUS.md](STATUS.md) | Where are we right now? What is next? | After every finished task and at the end of every session |
| [roadmap.md](roadmap.md) | What are the modules and how far along is each? | When a module changes status |
| [modules/](modules/) | What exactly does this module need, and which tasks are done? | As each task is finished |
| [session-log.md](session-log.md) | What happened in each session, and why? | At the end of every session |

## Starting a session

1. Read [STATUS.md](STATUS.md).
2. Open the active module file it names.
3. Read the design docs listed under that module's "Read first".
4. Check [open questions](../open-questions.md) for blockers on the next task.
5. Pick up the task marked next. If STATUS and the module file disagree, trust the module file's checkboxes and fix STATUS.

## Working on a task

- Tasks have IDs like `M1-T03`. Use the ID in commit messages.
- Do the tasks in the order listed unless the module file says they are independent.
- If a task turns out to need something not listed, add it to the module file as a new task before doing it.
- If a task needs a design change, change the design doc and log it in [decisions.md](../decisions.md) in the same commit.
- If a task hits an open question marked Blocks, stop that task, note it in STATUS, and move to an unblocked task or ask.

## Definition of done for a task

- The code does what the task says.
- Tests cover it and pass locally and in CI.
- [Project-specific requirement, for example: user-facing text exists in every supported language.]
- The doc that describes the behaviour is still true, or was updated.
- The task's checkbox is ticked in the module file.

## Definition of done for a module

- Every task is ticked.
- Every acceptance criterion in the module file has been checked by hand and is ticked.
- The roadmap status is set to Done with the date.
- STATUS points at the next module.

## Ending a session

1. Tick finished tasks. For a half-finished task, leave it unticked and write where it stands under the module's Notes.
2. Update STATUS: last done, next up, blockers, anything left in a broken state.
3. Append an entry to the session log.
4. Commit and push.

## Status words

| Status | Meaning |
| --- | --- |
| Not started | No task begun |
| In progress | At least one task begun, not all done |
| Blocked | Cannot proceed until an open question is answered; the question ID is given |
| Done | All tasks and acceptance criteria ticked |

## Commits and branches

- One task per commit where practical. Message format: `M1-T03: short description`.
- Doc-only commits use `docs: short description`.
- Never commit secrets or real personal data. Seed data is invented.
