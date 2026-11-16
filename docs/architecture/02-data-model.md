# Data model

Seventeen tables cover the MVP.

## Conventions

- IDs are UUIDs.
- Money is stored as integer minor units with a currency code.
- Nothing financial is ever updated in place or deleted. `ledger_entry`, `payment_event`, `verification_review` and `audit_log` are append-only, enforced by database permissions.
- Withdrawn or closed rows are marked with a timestamp, not deleted, unless a privacy rule requires deletion.
- Every table has `created_at`; mutable tables also have `updated_at`.

## Tables

### Accounts

| Entity | Key fields | Notes |
| --- | --- | --- |
| `user` | email, phone, password hash, locale, status, introduced by | One row per person. `introduced by` points at the user who brought them in. |
| `user_role` | user, role | Donor, presenter, verifier, admin |
| `organisation` | name, registration number, country, status | Optional parent of causes |

### Causes

| Entity | Key fields | Notes |
| --- | --- | --- |
| `cause` | presenter, organisation, beneficiary name, beneficiary relationship, beneficiary consent document, entered by, category, location, goal amount, currency, status, raised amount, verified until | `entered by` differs from `presenter` for assisted submissions. `status` follows the [cause lifecycle](../product/03-trust-model.md#cause-lifecycle). |
| `cause_translation` | cause, locale, title, summary, story | One row per language; at least one required |
| `cause_document` | cause, kind, storage key, checksum, uploaded by, visibility, reviewer-checked flag | Evidence. Private unless the presenter publishes a redacted copy. |
| `cause_update` | cause, disbursement (nullable), kind, attachments | Proof-of-use and general updates, with translations |
| `report` | cause, reporter (nullable), reason, status, resolved by | Public flagging |

### Trust

| Entity | Key fields | Notes |
| --- | --- | --- |
| `trust_link` | from user, to user, level, note, created at, withdrawn at | Directed. One live row per pair. Indexed on both ends for path search. |
| `cause_endorsement` | user, cause, statement, created at, withdrawn at | Trust in one cause, separate from trust in its presenter |
| `trust_invitation` | from user, to phone, email or user, cause (nullable), status | Rate-limited; expires if unanswered |

### Verification

| Entity | Key fields | Notes |
| --- | --- | --- |
| `verification_review` | cause, verifier, decision, checklist results (JSON), notes, decided at | Append-only; one row per decision |

### Money

| Entity | Key fields | Notes |
| --- | --- | --- |
| `donation` | cause, donor (nullable), amount, currency, status, provider reference, anonymous flag, trust path shown | Pending, paid, failed, refunded |
| `payment_event` | provider, event ID (unique), payload, processed at | Raw webhook log for idempotency |
| `ledger_entry` | account, cause, donation or disbursement, debit, credit, created at | Double-entry, append-only |
| `disbursement` | cause, amount, status, requested by, approved by, payout reference | Requested, approved, paid, rejected |

### Audit

| Entity | Key fields | Notes |
| --- | --- | --- |
| `audit_log` | actor, action, entity, before, after, IP, created at | Every staff action, every status change, every evidence view, every trust link change |

## Derived values

- A cause's `raised amount` is a cached figure. The ledger is the truth, and the nightly reconciliation job compares the two and alerts on any difference.
- A donation stores the trust path the donor was shown, so a failed vouch can be traced to the gifts it influenced.
- Presenter history is computed from `cause`, `disbursement`, `cause_update` and `report`. It has no table of its own.
