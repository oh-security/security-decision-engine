# External Disclosure Checklist

This checklist defines what information may be shared externally
and what must remain internal when presenting the Security Decision Engine
to potential acquirers or partners.

---

## ✅ OK to Share (External)

### High-level Concept
- Execution-free Security Decision Engine
- API-first, non-binding recommendations
- Phase2 complete (evaluation only)

### Architecture (Abstract)
- Detection → Decision → Human / External System
- No execution, enforcement, or UI
- Audit-ready (DecisionEvents)

### Contracts & Interfaces
- OpenAPI specification (Phase2)
- Decision types: show / suppress / snooze
- Human-defined policies (JSON format)

### Documentation
- README.md (Responsibility Boundary, API Boundary)
- Phase2 completion declaration
- Acquisition target positioning
- Valuation rationale (high-level)

### Positioning Statements
- “Safe to embed”
- “Low integration risk”
- “Execution remains external”

---

## ⚠️ Share with Caution (Controlled Disclosure)

- High-level AWS architecture (Lambda, API Gateway, DynamoDB)
- Sample JSON (policies, events) with generic identifiers
- Non-production demo endpoints (if any)

**Conditions**
- No customer identifiers
- No account IDs or ARNs
- No production URLs

---

## ❌ NOT OK to Share (Internal Only)

### Implementation Details
- Internal AWS account structure
- IAM policies and permissions
- Terraform / CloudFormation specifics
- Cost structures or AWS bills

### Security-Sensitive Information
- Internal threat models
- Abuse scenarios
- Rate limits and quotas
- Error handling specifics

### Commercial & Legal
- Internal valuation negotiations
- Target acquirer shortlists
- Legal advice or tax considerations

---

## Red Flags (Do Not Say)

- “Automatic remediation”
- “Enforcement engine”
- “We block resources”
- “We fix issues automatically”
- “This system guarantees security”

---

## Approved One-Liners

- “This system evaluates whether an action may be required.”
- “All outputs are non-binding recommendations.”
- “Execution and remediation are handled externally.”

---

## Final Check Before Sharing

- [ ] No execution language present
- [ ] No customer or account identifiers
- [ ] Responsibility boundary clearly stated
- [ ] Materials match Phase2 scope only
