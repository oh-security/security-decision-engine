Security Decision Engine

Phase2 – Evaluation Only

What this system is

This system is a Security Decision Engine that evaluates whether a security finding should be surfaced today based on human-defined policies.

It does not scan resources.
It does not execute actions.
It does not modify customer environments.

This system focuses on decision evaluation.

Responsibility Boundary

This system never executes actions.
All outputs are non-binding recommendations.
Customers remain fully responsible for any execution or remediation.

This engine:

evaluates findings against explicit policies

returns recommendations only

records why a decision was made

This engine never:

evaluates decisions

applies changes

performs remediation

modifies infrastructure

Why No Execution

Execution introduces:

legal liability

operational risk

trust erosion

Therefore, execution is explicitly out of scope.

This design allows the engine to be:

safely embedded into any security platform

reused across vendors and environments

evaluated without assuming customer risk

Decision Semantics

A decision represents today’s recommendation for a specific user.

Possible decision types:

show – surface the finding today

suppress – do not surface today

snooze – revisit at a future date

A decision typically includes:

a human-defined policy_id

a clear reason

a review_at timestamp for re-evaluation

If no decision is appropriate, the system may return no decision.

Returning zero decisions is a valid and expected outcome.

Policy Ownership

Policies are:

defined by humans

owned by customers

interpreted (not created) by this engine

Policies express intent.
The engine only evaluates them.

The system does not infer intent, learn intent, or override intent.

Audit & Explainability

All decision evaluations can be logged as immutable events.

These events exist to answer one question only:

“Why was this finding shown or hidden at that time?”

Events do not represent execution results.

Intended Usage

This engine is designed to sit between detection and action:

[ Findings / Alerts ]
        ↓
[ Security Decision Engine ]  ← this system
        ↓
[ Human or External System ]


Execution always happens outside this system.

## Non-Goals

The following are intentionally excluded:

- Any user interfaces or dashboards are explicitly out of scope for this system.
- Automatic remediation or execution of security actions.
- Enforcement mechanisms.
- Machine learning–based decision-making.

These capabilities may exist in downstream systems after integration or acquisition.

Summary (One Sentence)

This system does not execute or automate security actions.
It only determines whether an action may be required.
