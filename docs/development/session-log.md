# Session log

Append-only. One entry per working session, newest at the bottom. Keep entries short: what was done, what was decided, what is next. Detail belongs in the module files and design docs.

## Entry format

```text
## YYYY-MM-DD: short title

**Module:** M? or "design"
**Done:** what was finished, with task IDs
**Decided:** decision IDs added or changed, or "nothing"
**Left open:** anything half-finished or newly discovered
**Next:** the next task
```

---

## 2026-11-16: design and project setup

**Module:** design
**Done:**
- Wrote the product and architecture design: overview, flows, trust model, seeding plan, system, data model, API, languages, repo and tooling, payments, security and compliance.
- Set up the docs as the source of truth, with `CLAUDE.md` as the anchor.
- Created the development process, roadmap, six module files, decision log and open-questions list.

**Decided:** D-001 to D-010. Fifteen standing assumptions recorded (A-01 to A-15).
**Left open:** The design is a first draft and has not been reviewed by the product owner. Twenty-two open questions (Q-01 to Q-22).
**Next:** `M1-T01`, repository scaffold.
