# OPERATIONAL STATES

## Purpose of This File

This file defines the official Operational States of the Engineering Work Doctrine.

Its purpose is to govern how strict the doctrine's rules are, based on the **preciousness and reversibility** of the work's output.

The doctrine has three dimensions:

1. **Work Type** (Project, Feature, Refactoring, Bugfix, Task, Question) — determines the lifecycle path
2. **Proportionality** — determines process depth based on complexity
3. **Operational State** — determines how strict the rules are, based on output preciousness

This file defines the third dimension.

---

## The Hidden Problem This Solves

The doctrine's core rules were designed for production-grade work:

- 100% as Floor — assumes output is precious
- No workarounds — assumes workarounds create technical debt
- Rigid Payload — assumes output needs formal documentation
- Nothing modified without trace — assumes history is valuable
- First execution correct — assumes iteration is expensive
- Root cause not symptom — assumes you are fixing for the long term

All of these are correct **when the output is precious**. All of them are wrong **when the output is being formed**.

During active development:
- Migrations should be squashed, not preserved
- Code should be rewritten freely, not traced
- Workarounds are legitimate tools for exploration
- Iteration is the method, not a failure
- The "correct" architecture is unknown — you are discovering it

Applying production rules to formative work is like requiring a formal code review for a whiteboard sketch. It kills the very thing it is supposed to help.

The Operational State dimension resolves this by making the rules **scale with preciousness, not just complexity**.

---

## The Three Operational States

### Exploratory

**Definition:** The output of this work is throwaway. The goal is to learn whether something is viable, not to produce durable artifacts.

**When it applies:**
- Spikes and prototypes
- Feasibility investigations
- "Is this even possible?" work
- Technology evaluation
- Architecture exploration before commitment

**What matters:** Understanding gained. The code is disposable.

**What does not matter:** Code quality, traceability, test coverage, migration history, formal documentation.

**Key behaviors:**
- Process is minimal — classify and proceed
- Output is explicitly labeled as throwaway
- Workarounds are legitimate tools
- No Rigid Payload required
- No migration tracking
- No traceability required
- Iteration is expected and encouraged
- The AI should warn the user if they start treating exploratory output as durable

---

### Formative

**Definition:** The output of this work is being shaped. It matters now, but it will be rewritten or consolidated before becoming durable. The history of how we got here is not valuable — only the final state is.

**When it applies:**
- Active development before production
- Building a new feature that is still being shaped
- Iterating on architecture that hasn't been frozen
- Any work where the shape is still being discovered

**What matters:** The final state. The shape. The understanding.

**What does not matter:** The history of intermediate states. Traceability of each change. Migration sequence (until stabilization).

**Key behaviors:**
- Discovery and classification still apply (these are always required)
- Consolidation is encouraged — squash migrations, rewrite freely, clean up
- Workarounds are allowed but must be noted (so they can be removed during consolidation)
- Rigid Payload is required only for changes that are being committed as semi-permanent
- 100% criterion means "100% of current understanding" — not "100% production-ready"
- Iteration is expected — first execution does not need to be correct
- Root cause analysis applies when committing, not when experimenting
- The AI should track workarounds and experimental code so they can be cleaned during consolidation

---

### Stable

**Definition:** The output of this work is precious. It is either in production, preparing for production, or needs to be treated as if it were. The history of changes is valuable. Full doctrine applies.

**When it applies:**
- Production systems
- Pre-production systems being hardened
- Any system where changes are expensive to reverse
- Any system with real users or real data
- Any system where traceability is required (audit, compliance, blame)

**What matters:** Everything. The final state AND the history. Reversibility. Traceability. Quality.

**Key behaviors:**
- Full doctrine applies — all rules, all principles, all protocols
- 100% as Floor is non-negotiable
- Rigid Payload is mandatory for all implementation work
- No workarounds — resolve root cause
- Nothing modified without trace
- Migrations are ordered, non-destructive, and reversible
- First execution must be correct
- Full traceability required

---

## State Transitions

```
Exploratory ⇄ Formative ⇄ Stable
(throwaway)    (shaping)    (precious)
```

### Exploratory → Formative

**When:** The user decides to keep the work. What was a spike becomes a real feature.

**What happens:**
- The exploratory output is evaluated: what did we learn? What is worth keeping?
- A decision is made: "we are now building this for real"
- The work transitions to Formative state
- The exploratory code may be kept as a reference, rewritten, or discarded
- The AI must announce the transition explicitly

**This is a two-way door.** You can go back to Exploratory if Formative work reveals the shape is wrong.

---

### Formative → Stable (The Consolidation Moment)

**When:** The work's shape has been found. It is time to harden it for production or long-term durability.

**This is a one-way door.** Once you stabilize, you cannot go back to squashing migrations or rewriting freely. If you need to, you must declare a formal retreat to Formative with explicit justification.

**The Consolidation Moment ritual:**

**Core steps (always required):**

1. **Squash** all migrations into a clean, ordered sequence — each migration does exactly what it needs to do, in the right order, with no intermediate noise
2. **Remove** all workaround code — every workaround noted during Formative must be resolved or explicitly accepted as permanent
3. **Remove** all debug, experimental, and dead code
4. **Clean** the architecture — remove unused abstractions, simplify where possible
5. **Freeze** the API surface — the external interface is now stable and changes require formal process (see `32_API_GOVERNANCE_PROTOCOL.md`)
6. **Write** the tests that will protect the stabilized code — characterization tests, unit tests, integration tests as appropriate (see `23_TESTING_STRATEGY_PROTOCOL.md`)
7. **Document** the final state — the architecture, the decisions, the constraints (see `29_DOCUMENTATION_PROTOCOL.md`)
8. **Declare** explicitly: "This work enters Stable state"

**Mega-tech protocol steps (required when the protocol applies):**

9. **Technical debt review** — review all intentional debt incurred during Formative. Pay off or explicitly accept each item. Enter remaining debt into the Debt Register. No untracked debt may survive into Stable (see `27_TECHNICAL_DEBT_PROTOCOL.md`)
10. **Data governance review** — all data touched by the work is classified. Access control is verified. Retention policy is defined. Encryption is verified. Audit trail is confirmed for Confidential/Restricted data (see `33_DATA_GOVERNANCE_PROTOCOL.md`)
11. **Security review** — the work is security-reviewed at the appropriate level (Level 1 automated, Level 2 manual if touching auth/data/external interfaces, Level 3 threat model if new system or major change) (see `26_SECURITY_REVIEW_PROTOCOL.md`)
12. **Observability verification** — logs, metrics, traces, alerts, and dashboards are present for the stabilized surface area (see `25_OBSERVABILITY_PROTOCOL.md`)
13. **Dependency verification** — all dependencies are pinned to exact versions, lockfiles are committed, security scan is clean (see `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`)
14. **Architecture decisions recorded** — all significant decisions made during Formative have ADRs (see `24_ARCHITECTURE_DECISION_RECORDS.md`)
15. **Incident response readiness** — if the work is deployed to production, the rollback plan is verified and the incident response procedure is documented (see `30_INCIDENT_RESPONSE_PROTOCOL.md`)
16. **Quality gates verification** — all applicable quality gates pass (test gate, security gate, documentation gate, deployment gate, ADR gate, debt gate, dependency gate, data governance gate) (see `31_QUALITY_GATES.md`)
17. **Metrics definition** — success metrics are defined and collection mechanisms are in place (DORA metrics, doctrine compliance metrics) (see `34_METRICS_FEEDBACK_LOOP.md`)

The Consolidation Moment is complete only when all applicable steps are done. A step that does not apply (e.g., data governance for a system with no data, incident response for a non-deployed system) may be explicitly marked as "not applicable" — but it may not be silently skipped.

The Consolidation Moment is a deliberate act, not a gradual drift. The AI must not let work "accidentally" become Stable. The transition must be announced and the ritual completed.

---

### Stable → Formative (Retreat)

**When:** A fundamental rethink is needed. The architecture is wrong. The shape is wrong. Incremental changes won't fix it.

**What happens:**
- The AI must declare the retreat explicitly with justification
- The user must approve the retreat
- The work returns to Formative state
- Stable rules no longer apply — but the history of what was Stable is preserved
- A new Consolidation Moment will be needed to return to Stable

**This is rare and should not be undertaken lightly.** It means the previous stabilization was premature or the requirements have fundamentally changed.

---

## How Rules Change by State

| Rule | Exploratory | Formative | Stable |
|---|---|---|---|
| Classify before acting | Yes | Yes | Yes |
| Discovery | Minimal | Light | Standard (per work type) |
| 100% as Floor | N/A (throwaway) | "100% of current understanding" | Full 100% |
| Rigid Payload | No | Only on committed changes | Yes (always) |
| No workarounds | Allowed (tool) | Allowed with note | Prohibited |
| Traceability | None | Only final state | Full |
| First execution correct | No (iteration expected) | No (iteration expected) | Yes |
| Root cause not symptom | N/A | When committing | Yes |
| Migrations | N/A | Squash freely | Ordered, reversible |
| Nothing modified without trace | No | No (rewrite freely) | Yes |
| Work Agreement | Not required | Light (Task Brief level) | Standard (per work type) |
| Readiness check | Not required | Light | Standard |
| Enforcement instruments | Not required | When committing | Yes |

---

## Per-Item State

The Operational State is **per-work-item, not per-project**.

A single project can have work items in different states:

| Work Item | State | Why |
|---|---|---|
| Core authentication module | Stable | Live, serving users, full process |
| New reporting feature | Formative | Being built, iterating, migrations squashable |
| Spike for real-time updates | Exploratory | Throwaway, testing viability |
| Bug in auth module | Stable | Fixing live code, full Fix Path |
| Refactoring of reporting feature | Formative | Part of active development |

This means the AI must determine the state of **each work item**, not just the project. When a user says "fix the login bug," the AI must determine: is this a Stable login module (full Fix Path) or a Formative one (just rewrite the broken part)?

---

## State Determination

### How the AI Determines State

The AI determines the Operational State by examining:

1. **Is the system live?** If yes → Stable. If no → continue.
2. **Does the system have real users or real data?** If yes → Stable. If no → continue.
3. **Is the output throwaway (spike, prototype, investigation)?** If yes → Exploratory.
4. **Is the shape still being discovered (active iteration, architecture not frozen)?** If yes → Formative.
5. **Is the system being hardened for production?** If yes → Stable.
6. **If unclear → default to Stable** (safest assumption, preserves doctrine's existing behavior).

### State Declaration

The state should be declared at the start of a work session, alongside the work type classification:

> "This work is classified as: **Feature** (work type) in **Formative** state (operational state)."

If the state is not declared, the AI must infer it and state its inference explicitly. If the AI cannot infer it, it defaults to Stable.

### State Can Change Mid-Work

If, during execution, it becomes clear that the state is wrong (e.g., what seemed Formative is actually Stable because the system is live), the AI must:
- stop and re-declare the state
- announce the change explicitly
- switch to the correct rule set
- not silently continue with the wrong rules

This mirrors Rule 0.4 (Re-Classify When the Work Type Materially Changes).

---

## Interaction with Existing Doctrine

### Proportionality (Principle 1)

Operational State extends proportionality. Now the doctrine scales with **two** factors:
- **Complexity** → how much process (handled by Work Type and Proportionality)
- **Preciousness** → how strict the rules are (handled by Operational State)

A complex system in Formative state needs deep understanding but relaxed rules. A simple system in Stable state needs light process but strict rules. These are independent dimensions.

### 100% as Floor (Principle 2)

The 100% criterion is now state-dependent:
- **Exploratory:** 100% does not apply — the output is throwaway
- **Formative:** 100% means "100% of current understanding" — you understand what you built, even if it will change
- **Stable:** Full 100% — the work is complete, verified, and production-ready

This does not weaken 100% as Floor. It refines what "100%" means in different contexts.

### Rigid Payload (Rule 6.6)

The Rigid Payload requirement is now state-dependent:
- **Exploratory:** Not required
- **Formative:** Required only for changes being committed as semi-permanent
- **Stable:** Always required for implementation work

### No Workarounds (Rule 6.2)

The workaround prohibition is now state-dependent:
- **Exploratory:** Workarounds are legitimate tools for exploration
- **Formative:** Workarounds are allowed but must be noted for later removal
- **Stable:** Workarounds are prohibited — resolve root cause

---

## State Tracking

The Operational State must be tracked in the Work State File (see `13_PROJECT_SESSION_TEMPLATE.md`). Each work item records:

- Current Operational State
- State history (when it transitioned and why)
- Workarounds noted during Formative (for cleanup during Consolidation Moment)
- Whether the Consolidation Moment has been completed

---

## Anti-Patterns Related to Operational State

### Applying Stable Rules to Formative Work
Using production-grade process on work that is still being shaped. This kills iteration speed and creates unnecessary ceremony.

**Corrective:** Classify the state correctly and apply the appropriate rule set.

### Applying Formative Rules to Stable Work
Using relaxed rules on production code because "we're still developing it." This creates untraceable changes in live systems.

**Corrective:** If the system is live, it is Stable. Full process applies.

### Skipping the Consolidation Moment
Letting work "drift" from Formative to Stable without the explicit consolidation ritual. This leaves workarounds, debug code, and messy migrations in production.

**Corrective:** The Consolidation Moment is mandatory. No work enters Stable without it.

### Never Declaring Stable
Staying in Formative forever because "we're still iterating." This prevents the work from ever being properly hardened.

**Corrective:** At some point, the shape is found. Declare Stable and consolidate.

### Treating Exploratory Output as Durable
Building on top of spike code as if it were production code. This creates fragile systems built on throwaway foundations.

**Corrective:** If you decide to keep the work, transition to Formative and rebuild properly.

---

## Operational State Success Condition

The Operational State dimension has been applied successfully when:

- every work item has an explicit Operational State
- the rules applied match the state
- Formative work is allowed to iterate freely without production ceremony
- Stable work is treated with full doctrinal rigor
- the Consolidation Moment is performed before any work enters Stable
- state transitions are announced explicitly, never drifted silently
- per-item state is respected within projects that have mixed states

That is the official success condition of the Operational State dimension.

---

## Next File

Continue to:

`22_DISCOVERY_DIMENSION_PROTOCOL.md`
