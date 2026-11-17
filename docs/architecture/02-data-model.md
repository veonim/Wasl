# Data model

Fifteen tables cover the MVP. None of them holds money: Wasl records what people report was given and received, and never moves funds. See [giving](06-giving.md).

## Conventions

- IDs are UUIDs.
- Amounts are stored as integer minor units with a currency code.
- `verification_review` and `audit_log` are append-only, enforced by database permissions.
- A gift's amount is never edited after the presenter confirms it; corrections are new rows that reference the old one.
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
| `cause` | presenter, organisation, beneficiary name, beneficiary relationship, beneficiary consent document, entered by, category, location, goal amount, currency, status, confirmed amount, reported amount, verified until | `entered by` differs from `presenter` for assisted submissions. `status` follows the [cause lifecycle](../product/03-trust-model.md#cause-lifecycle). |
| `cause_translation` | cause, locale, title, summary, story | One row per language; at least one required |
| `cause_document` | cause, kind, storage key, checksum, uploaded by, visibility, reviewer-checked flag | Evidence. Private unless the presenter publishes a redacted copy. |
| `cause_update` | cause, kind, period covered, amount accounted for, attachments | Proof-of-use and general updates, with translations |
| `report` | cause, reporter (nullable), reason, status, resolved by | Public flagging |

### Giving

| Entity | Key fields | Notes |
| --- | --- | --- |
| `payment_method` | cause, kind (bank account, mobile wallet), account title, institution, account identifier, proof document, status, checked by, checked at | How donors pay the presenter directly. Shown only while the cause is Live. Any change resets `status` to pending review. |
| `gift` | cause, donor (nullable), amount, currency, method, transfer reference, given on, status, recorded by, trust path shown, anonymous flag, corrects (nullable) | A record that money was sent directly to the presenter. `status`: reported, confirmed, disputed, withdrawn. `recorded by` is the donor, or the presenter for gifts that arrived unrecorded. |

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

### Audit

| Entity | Key fields | Notes |
| --- | --- | --- |
| `audit_log` | actor, action, entity, before, after, IP, created at | Every staff action, every status change, every evidence view, every trust link change, every payment-method change |

## Derived values

- A cause's `confirmed amount` is the sum of its confirmed gifts and is the figure shown against the goal. `reported amount` is the sum of gifts recorded but not yet confirmed. Both are cached and recomputed from `gift` rows.
- A gift stores the trust path the donor was shown, so a failed vouch can be traced to the gifts it influenced.
- Presenter history is computed from `cause`, `gift`, `cause_update` and `report`. It has no table of its own.

## What is deliberately absent

There is no payment, transaction, ledger, balance, payout or refund table. If a change seems to need one, it conflicts with decision D-013 and must not be built.
