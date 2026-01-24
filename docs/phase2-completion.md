# Security Decision Engine — Phase2 Complete

## What it is
An API-first Security Decision Engine that evaluates whether a security finding
should be surfaced today, based on human-defined policies.

All outputs are non-binding recommendations.

---

## What it intentionally does NOT do
- No execution
- No enforcement
- No UI

---

## What is complete in Phase2
- Human-defined policies (JSON)
- Deterministic decision types: show / suppress / snooze
- Append-only audit logs (DecisionEvents)
- OpenAPI contract (integration-ready)

---

## Responsibility Boundary
Execution and remediation remain entirely outside this system.

---

## Intended Integration
This engine is designed to sit upstream of notification,
alerting, or workflow systems.

It evaluates whether a given security finding
should be shown, suppressed, or deferred,
but does not trigger any action itself.

Integration is expected to be performed by the consuming system,
which remains fully responsible for execution,
remediation, and user-facing behavior.
