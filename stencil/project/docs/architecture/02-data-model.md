# Data model

[N] tables cover the first release.

## Conventions

- IDs are [UUIDs / integers].
- [How amounts, dates and times are stored.]
- [Which tables are append-only, and how that is enforced.]
- [Whether rows are deleted or marked closed.]
- Every table has `created_at`; mutable tables also have `updated_at`.

## Tables

### [Area]

| Entity | Key fields | Notes |
| --- | --- | --- |
| `[table]` | [fields] | [rules, relationships, visibility] |

## Derived values

- [Any cached or computed value, and where its truth comes from.]

## What is deliberately absent

[Tables someone might expect that must not exist, and the decision that rules them out. Delete this section if there are none.]
