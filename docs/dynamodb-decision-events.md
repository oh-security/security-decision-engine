# DynamoDB: DecisionEvents

## Purpose
Append-only audit log for **decision evaluations only**.
This table records *why* a decision was evaluated, not *what was executed*.

---

## Table Name
`DecisionEvents`

---

## Keys

- **Partition Key (PK)**: `user_id` (String)  
- **Sort Key (SK)**: `evaluated_at` (String, ISO8601 UTC)

This key design enables:
- Chronological audit of decisions per user
- Append-only logging
- Simple, deterministic access patterns

---

## Required Attributes

| Attribute | Type | Description |
|---|---|---|
| `user_id` | String | Target user identifier |
| `evaluated_at` | String | Evaluation timestamp (ISO8601 UTC) |
| `date_jst` | String | Evaluation date in JST (YYYY-MM-DD) |
| `decision_type` | String | `show` / `suppress` / `snooze` |
| `tip_id` | String | Identifier of the evaluated tip |
| `severity` | String | `HIGH` / `MEDIUM` / `LOW` |
| `policy_id` | String | Human-defined policy that matched |
| `reason` | String | Human-readable explanation |
| `recommendation` | Boolean | Always `true` (non-binding) |
| `policy_set_hash` | String | Fingerprint of policy set at evaluation time |
| `engine_version` | String | Engine version identifier |
| `source` | String | Invocation source (e.g. `api`) |

---

## Optional Attributes

| Attribute | Type | Description |
|---|---|---|
| `review_at` | String | Recommended review date for `suppress` / `snooze` |

---

## policy_set_hash

`policy_set_hash` represents a cryptographic fingerprint of the entire policy set
used at the time of decision evaluation.

The hash is computed by:
1. Collecting all policy JSON files under `policies/`
2. Normalizing their content (stable key ordering, whitespace removed)
3. Concatenating the normalized policies
4. Computing a SHA-256 hash of the result

This allows the exact policy set used for a decision to be verified later,
even if individual policies are modified after the fact.

---

## Access Patterns

- Retrieve all decisions for a user (chronological):
  - PK = `user_id`
  - SK ordered by `evaluated_at`

No additional indexes are required for Phase2.

---

## Non-Goals

- No execution status is recorded.
- No update or delete operations (append-only).
- No automatic remediation tracking.
- No GSIs required for Phase2.

---

## Notes

This table is designed for **auditability and explainability**.
It intentionally avoids storing any execution results or side effects.
