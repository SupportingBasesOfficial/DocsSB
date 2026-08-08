# ARCHITECTURE DECISION RECORDS

## Purpose of This File

This file defines the official Architecture Decision Records (ADR) protocol of the Engineering Work Doctrine.

Its purpose is to ensure that significant decisions are recorded with context, alternatives, and rationale — so that the reasoning behind a decision survives long after the decision itself.

Decisions are made during every work item. Without durable records, the rationale is lost. The next person to touch the code — whether a new team member or a new AI instance — sees **what** was decided but never **why**. They are forced to reverse-engineer intent from code, or worse, undo a decision that was made for reasons they cannot see.

This is standard practice at every mega-tech company. ADRs are the mechanism that turns decisions from ephemeral conversation into durable artifacts.

---

## What Requires an ADR

Not every decision needs an ADR. Trivial decisions — naming a local variable, choosing a loop construct, picking a utility function — do not need to be recorded. ADRs exist for decisions that have **weight**: decisions that shape the system, constrain future work, or affect more than the immediate code.

ADRs are required for:

- **Architecture decisions** — choosing a pattern, structure, or approach (e.g., monolith vs. microservices, event-driven vs. request-response, layered vs. hexagonal)
- **Technology choices** — frameworks, libraries, databases, infrastructure (e.g., choosing PostgreSQL over MySQL, React over Vue, Kafka over RabbitMQ)
- **API design decisions** — contract shape, versioning strategy, error handling (e.g., REST vs. gRPC, semantic versioning vs. header-based versioning, error envelope format)
- **Data model decisions** — schema, storage, partitioning (e.g., normalized vs. denormalized, single-table vs. multi-table, partition key selection)
- **Security decisions** — auth model, encryption, access control (e.g., OAuth2 vs. session-based, field-level encryption, RBAC vs. ABAC)
- **Operational decisions** — deployment strategy, observability approach (e.g., blue-green vs. canary, push vs. pull metrics, structured logging format)
- **Decisions that are hard to reverse** — anything where undoing the decision would require significant rework
- **Decisions that affect multiple teams** — anything where the decision creates a constraint or expectation for other teams

If a decision does not fall into any of these categories, it does not need an ADR. When in doubt, write one — the cost of an unnecessary ADR is low; the cost of a lost decision is high.

---

## ADR Format

Each ADR must contain the following sections, in this order:

- **ADR ID** — a sequential number (ADR-001, ADR-002, ADR-003, etc.). Numbers are never reused, even if an ADR is deprecated or superseded.
- **Date** — when the decision was made (not when the ADR was written, if those differ).
- **Status** — the current lifecycle state of the ADR (see ADR Lifecycle below).
- **Context** — the situation that prompted the decision. The constraints, the forces, the problem being solved. This section answers: *what is the problem, and why does it need a decision now?*
- **Decision** — what was decided. This section answers: *what are we doing?* It should be stated clearly and unambiguously.
- **Alternatives Considered** — what other options were evaluated, and why they were rejected. This section is critical. Without it, the ADR records the decision but not the reasoning. A future reader who questions the decision needs to see that alternatives were considered, not that the decision was made in ignorance.
- **Consequences** — what follows from this decision. This includes positive consequences (what we gain), negative consequences (what we lose or risk), and neutral consequences (what is now constrained or implied). This section answers: *what does this decision cost, and what does it enable?*
- **Related ADRs** — links to related decisions, if any (e.g., an ADR that this one builds on, an ADR that this one supersedes, an ADR that constrains this one).

An ADR that is missing any of these sections is incomplete. An ADR without alternatives considered is not an ADR — it is a statement of preference.

---

## ADR Storage

ADRs are stored in the project directory under `docs/adr/` or an equivalent location appropriate to the project's structure.

Each ADR is a single markdown file named `ADR-NNN-short-title.md`, where:

- `NNN` is the zero-padded sequential number (001, 002, 003, etc.)
- `short-title` is a kebab-case description of the decision (e.g., `ADR-001-use-postgresql-for-primary-database.md`)

Example directory structure:

```
project/
  docs/
    adr/
      ADR-001-use-postgresql-for-primary-database.md
      ADR-002-event-driven-communication-between-services.md
      ADR-003-oauth2-for-external-api-auth.md
```

ADRs are never deleted. Deprecated and superseded ADRs remain in the directory with their status updated. The ADR history is part of the project's institutional memory.

---

## ADR Lifecycle

Every ADR has a lifecycle state. The state is recorded in the ADR's **Status** field and updated as the decision evolves.

- **Proposed** — The ADR is written but not yet accepted. The decision is under review. The team has not committed to it. A proposed ADR may be revised, withdrawn, or accepted.
- **Accepted** — The ADR is accepted and the decision is binding. The team has committed to the decision. Work proceeds according to the decision. An accepted ADR may later be deprecated or superseded, but it is never silently ignored.
- **Deprecated** — The ADR is no longer relevant. The decision it records is no longer in effect, but it has not been replaced by a new decision. This happens when the context that prompted the decision no longer exists (e.g., a feature was removed, a system was decommissioned).
- **Superseded** — The ADR has been replaced by a newer ADR. The superseding ADR must reference the superseded ADR, and the superseded ADR must reference the superseding ADR. The relationship is bidirectional.

State transitions are explicit. An ADR does not drift from Accepted to Deprecated — it is explicitly marked. When an ADR is superseded, the new ADR must state: *"This ADR supersedes ADR-NNN"* and the old ADR must be updated to state: *"This ADR is superseded by ADR-NNN."*

---

## When to Write an ADR

ADRs are written when significant decisions are made. Within the doctrine's lifecycle, this happens at specific points:

- **During consolidation (Stage 2)** — when architectural implications become clear. Consolidation is where the shape of the solution is determined. If an architectural decision is made during consolidation, it gets an ADR.
- **During delivery (Stage 5)** — when implementation decisions are made. Delivery often involves decisions that were not foreseen during consolidation: a library choice, an error handling strategy, a data structure. If the decision is significant, it gets an ADR.
- **During evolution (Stage 6)** — when the system changes class. Evolution decisions are inherently significant: they alter the system's structure, scale, or operational model. These always get ADRs.
- **Any time a significant decision is made** — the lifecycle stages are the common points, but a significant decision can be made at any time. If a decision meets the criteria in "What Requires an ADR," it gets an ADR regardless of when it was made.

ADRs are not written during discovery (Stage 1). Discovery is about understanding the problem, not deciding the solution. Decisions made during discovery are preliminary and may not survive into consolidation.

---

## ADR and the Work Agreement

Significant ADRs should be referenced in the Work Agreement.

The Work Agreement and the ADR serve complementary purposes:

- **The Work Agreement** captures **what** was decided — the decision itself, as a binding commitment for the work item.
- **The ADR** captures **why** it was decided — the context, the alternatives, the reasoning.

A Work Agreement that says "we will use PostgreSQL" is a commitment. An ADR that says "we chose PostgreSQL over MySQL and DynamoDB because of X, Y, and Z" is the reasoning. The Work Agreement without the ADR is a decision without rationale. The ADR without the Work Agreement is rationale without commitment.

Not every ADR needs to be referenced in the Work Agreement — only the significant ones, the ones that shape the work. The Work Agreement should reference the ADR by ID (e.g., *"Database: PostgreSQL (see ADR-001)"*).

---

## ADR and Operational State

The ADR protocol scales with the Operational State, like all doctrine protocols:

- **Exploratory** — ADRs are not required. Exploratory work is throwaway. Decisions made during exploration are provisional and may not survive. Writing ADRs for throwaway decisions is ceremony that kills exploration.
- **Formative** — ADRs are required for decisions that will survive into Stable. Formative work is shaping the system, and the decisions made during formation will become the system's structure. If a decision will persist, it gets an ADR. If it is still being explored, it does not.
- **Stable** — ADRs are required for all significant decisions. Stable work is production-grade. Every decision that meets the criteria in "What Requires an ADR" gets an ADR. No exceptions.

This scaling prevents two failure modes:

1. Requiring ADRs in Exploratory — kills exploration with ceremony
2. Not requiring ADRs in Stable — loses decisions that will persist for years

---

## ADRs in the Rigid Payload

The Rigid Payload (defined in `20_ENFORCEMENT_LAYER.md`) has four sections. ADRs are referenced in the **Diagnóstico** section — the diagnosis explains why the change is necessary, and the ADR provides the decision context.

The Diagnóstico section must reference any ADRs that informed the work:
- **ADR IDs** — list any ADRs that were created or superseded during this work item
- **Decision context** — if a significant decision was made during this work, an ADR must exist and be referenced here

If no significant decisions were made (e.g., a straightforward bugfix), the Diagnóstico section may state: "No ADRs — no significant architectural decisions in this work item."

This ensures that decisions are not made silently. Every significant decision must have a traceable ADR, and the Rigid Payload connects the work to the decisions that shaped it.

---

## ADR Anti-Patterns

The following are ADR anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **No ADR for a significant decision** — a decision that affects architecture, data flow, security, or external interfaces is made without an ADR. The decision exists only in someone's head.
- **Retroactive ADR** — an ADR written long after the decision was made, reconstructed from memory or code. The ADR documents what happened, not what was decided. Context is lost.
- **ADR as documentation, not decision** — an ADR that describes the current state without explaining the alternatives considered, the criteria, and the trade-offs. It is a description, not a decision record.
- **ADR that never gets superseded** — decisions change, but the ADR remains. The code says one thing, the ADR says another. Stale ADRs are worse than no ADRs because they mislead.
- **ADR with no context** — an ADR that states the decision but not why it was made. Without context, the decision cannot be evaluated when circumstances change.
- **ADR for trivial decisions** — an ADR for a decision that doesn't affect architecture (e.g., variable naming, formatting). ADRs have overhead; trivial decisions don't need them.

---

## ADRs and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that all significant architectural decisions made during Formative have ADRs recorded. No work enters Stable state with undocumented architectural decisions.

---

## Protocol Success Condition

The ADR protocol has been applied successfully when:

- every significant decision has a recorded ADR
- each ADR contains all required sections (ID, Date, Status, Context, Decision, Alternatives Considered, Consequences, Related ADRs)
- no ADR is missing the Alternatives Considered section
- ADRs are stored in the project's `docs/adr/` directory with consistent naming
- deprecated and superseded ADRs remain in the directory with updated status
- superseded ADRs reference their superseding ADRs and vice versa
- significant ADRs are referenced in the Work Agreement
- the depth of ADR usage matches the Operational State (none in Exploratory, selective in Formative, complete in Stable)
- any new team member or AI instance can understand not just **what** was decided but **why**

That is the official success condition of the ADR protocol.

**Anti-pattern:** See ANTI-PATTERN 32 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.3 in `08_DECISION_RULES.md`.

---

## Next File

The next file in the doctrine is `25_OBSERVABILITY_PROTOCOL.md`.
