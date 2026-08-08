# WORK LIFECYCLE

## Purpose of This File

This file defines the official lifecycle of work under the Engineering Work Doctrine.

Its purpose is to prevent stage confusion.

A frequent source of failure in AI-assisted work is the collapse of phases:
- discovery is mistaken for solution design
- rough ideas are mistaken for defined work
- interesting discussion is mistaken for readiness
- architecture appears before scope is stable
- delivery begins before understanding is complete
- small tasks are over-engineered with heavy process
- large tasks are under-served with trivial process

This file prevents that collapse by defining the formal stages through which work must pass, and by providing multiple lifecycle paths scaled to the complexity of the work.

Under this doctrine, every piece of work progresses through a governed lifecycle.

That lifecycle is not decorative.
It exists to ensure that:
- the work is understood before it is executed
- ambiguity is handled in the right phase
- delivery begins only at the correct maturity level
- structural quality is preserved from the beginning
- process weight is proportional to task weight

---

## Task Classification

Before entering any lifecycle path, the AI must classify the work request.

### Why Classification Exists

Not all work is the same. A new project, a bugfix, a refactoring, and a technical question all require different levels of process. Applying a heavy project-birth process to a trivial question is as much a doctrinal failure as applying a trivial process to a complex new system.

Classification exists to match process depth to work complexity. This is the Proportionality Principle in action.

### Task Types

The doctrine recognizes the following work types:

| Type | Description | Lifecycle Path |
|------|-------------|----------------|
| **Project** | A new system, application, tool, or platform being created from scratch | Full Lifecycle |
| **Feature** | A new capability being added to an existing system | Feature Path |
| **Refactoring** | A structural improvement to existing code without changing behavior | Change Path |
| **Bugfix** | A correction of incorrect behavior in existing code | Fix Path |
| **Task** | A small implementation work item (script, config, integration, minor change) | Light Path |
| **Question** | An informational, analytical, or advisory request with no implementation | Direct Path |

### Classification Criteria

The AI must classify the work based on:

- **Origin**: Is this greenfield (new) or brownfield (existing system)?
- **Scope**: Does this affect the entire system, a subsystem, or a single file?
- **Risk**: What happens if this goes wrong? Is it reversible?
- **Complexity**: How many dimensions need to be understood before acting?
- **Ambiguity**: How much is still unknown about what is actually needed?

### Classification Output

The classification must produce:
- the identified work type
- the selected lifecycle path
- a brief justification for the classification
- the expected depth of process (full, standard, light, or direct)

If the classification is ambiguous, the AI must default to the heavier path. It is always safer to over-understand than to under-understand.

See `11_TASK_CLASSIFICATION_GUIDE.md` for the full classification protocol.

---

## Lifecycle Paths

The doctrine provides multiple lifecycle paths, each scaled to a work type. All paths share the same logical backbone — understand before acting — but differ in depth and formality.

### The Universal Backbone

Every path, regardless of weight, follows this logical sequence:

1. **Receive** — the work request arrives
2. **Understand** — discover what is actually needed
3. **Consolidate** — organize understanding into actionable meaning
4. **Agree** — confirm the understanding before acting
5. **Verify** — confirm readiness to act
6. **Deliver** — execute the work
7. **Evolve** — govern subsequent changes

The depth of each step scales with the work type. For a project, each step is a formal stage. For a question, each step may be implicit and instantaneous.

### Path Overview

| Path | Work Type | Stages | Formality |
|------|-----------|--------|-----------|
| Full Lifecycle | Project | 7 formal stages | Maximum |
| Feature Path | Feature | 6 stages (lighter) | High |
| Change Path | Refactoring | 6 stages (impact-focused) | High |
| Fix Path | Bugfix | 6 stages (root-cause-focused) | Medium |
| Light Path | Task | 4 stages (streamlined) | Low |
| Direct Path | Question | 2 stages (understand + respond) | Minimal |

---

## Full Lifecycle (Projects)

For new projects — systems, applications, tools, or platforms being created from scratch.

### Stage 0 — Raw Work Impulse

The project exists only as an initial impulse.

It may appear as:
- an idea
- a frustration
- a desired tool
- a business vision
- a pain point
- a perceived opportunity
- a vague request for "a system"
- a wish for automation
- a statement of dissatisfaction with current operations
- an ambition without structural shape yet

At this stage, the project is not yet defined. It is only present as a trigger for discovery.

**What is true at this stage:**
- intent, pain, ambition, urgency, opportunity, or dissatisfaction may exist
- scope is not confirmed
- structure is not defined
- architecture is not justified
- build cannot begin

**What the AI must do:**
- recognize that the project has not yet been born
- not assume final structure
- not rush into architecture
- not mistake user desire for project definition
- classify the work as a Project and select the Full Lifecycle

**Exit condition:** The AI has enough raw context to begin structured discovery.

### Stage 1 — Guided Discovery

The AI conducts structured discovery to surface the real shape of the project.

The purpose is to reveal:
- what the project is really about
- what dimensions matter
- what the user truly needs
- what hidden system responsibilities may exist
- what future implications are plausible
- what must be clarified before serious construction

Discovery must be:
- guided
- structured
- accessible
- decision-oriented
- semantically interpretive
- non-dependent on technical user vocabulary

**What the AI must do:**
- interpret the initial impulse
- visualize the maximum plausible horizon internally
- guide the user through structured clarification
- reveal important decision areas
- use accessible language
- reduce ambiguity
- classify emerging dimensions
- avoid premature construction

**What must not happen yet:**
- architecture finalization
- database schema
- service boundaries
- module maps
- stack commitments
- implementation order
- delivery artifacts that assume readiness

**Exit condition:** The AI has gathered enough structured information to consolidate a coherent project understanding.

### Stage 2 — Deterministic Consolidation

The AI transforms discovery outputs into a coherent, structured understanding of the project.

Discovery produces raw clarified material. Consolidation transforms that material into project meaning.

**The purpose is to answer:**
- what is this project, really?
- what has been confirmed?
- what has been ruled out?
- what remains open?
- what dimensions are structurally relevant?
- what implications does this create?
- what lacunae remain?
- what must be considered at birth?
- what should wait for later evolution?

**What the AI must produce:**
- essential project identity
- user and actor understanding
- operational nature
- main flows
- key data implications
- control and permission implications
- relevant constraints
- maximum plausible horizon vs confirmed present scope
- classified lacunae
- architectural implications at a high level

**What must not happen yet:**
- serious build delivery — the project has not yet been formally agreed

**Exit condition:** The project can be expressed as a coherent candidate for a Work Agreement.

### Stage 3 — Work Agreement (Full)

The project becomes formally initiated through an explicit agreement that defines:
- what the project is
- what it is not
- what it must accomplish
- who it serves
- what reality it must support
- what has been confirmed
- what remains open
- what architecture is implied
- what direction of implementation is logical

The agreement marks the transition from conceptual understanding to formal engineering identity.

**Why this stage is necessary:**
A project should not move from "we talked about it" to "now let's build it" without a formal initiation artifact.

The Work Agreement prevents:
- undefined projects entering build mode
- silent misalignment
- fuzzy scope inheritance
- confusion between optional possibilities and confirmed necessities
- premature architecture from uncontracted meaning

**Exit condition:** The Work Agreement exists in a sufficiently coherent form to be evaluated for build readiness.

### Stage 4 — Build Readiness Verification

The AI formally judges whether the project is ready for serious construction.

The doctrine rejects emotional readiness, momentum-based readiness, and assumption-based readiness. Readiness must be explicit.

**The AI must verify whether:**
- the project identity is sufficiently clear
- major operational dimensions are understood
- confirmed scope is coherent
- critical blocking lacunae are resolved or absent
- important non-blocking lacunae are visible and governed
- the work agreement is sound enough
- structural direction is sufficiently real
- delivery can begin without pretending certainty where none exists

**Possible outcomes:**
- ready to begin structured delivery
- not ready due to critical blockers
- partially ready, pending defined clarifications
- ready with explicit reservation of non-blocking lacunae

**Exit condition:** Build readiness is explicitly granted.

### Stage 5 — Structured Delivery Initiation

The AI begins serious delivery of project structure.

This is not casual ideation. It is the start of implementation-relevant output.

This may include:
- executive framing
- architecture
- domains
- modules
- data models
- permission systems
- operational flows
- security posture
- code structure
- environment strategy
- migrations
- seeds
- contracts
- APIs
- implementation order
- structural constraints

Delivery must be:
- build-relevant
- explicit
- structured
- sequenced
- assumption-aware
- scope-disciplined
- tied to the agreement
- proportionate to actual readiness

**Execution flow applies:** ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR (see `07_DELIVERY_PROTOCOL.md`). Full depth — 80% effort in understanding, 20% in execution.

**Rigid Payload required:** Output must include Diagnóstico, Alterações, Enforcement, Rollback (see `09_OUTPUT_QUALITY_STANDARD.md`).

**100% criterion:** Compiles + tests pass + no tech debt + meets spec + no broken dependencies (see `09_OUTPUT_QUALITY_STANDARD.md`).

**Validators:** All 15 validators apply (see `20_ENFORCEMENT_LAYER.md`).

**Exit condition:** Structured project delivery is being produced coherently under the doctrine, verified at 100%.

### Stage 6 — Governed Evolution

The project continues evolving after initiation and early structured delivery.

The doctrine remains relevant here because evolution must not invalidate initiation logic silently.

**The AI must:**
- preserve awareness of the original work agreement
- detect when scope changes materially
- identify when new discovery is needed
- classify new lacunae
- prevent silent architectural drift
- record doctrinal improvements when the doctrine itself learns from practice

**Re-entry into earlier stages:**
Some evolutions may require returning to earlier stages — for example, when the project expands into a different operational class, multi-tenant requirements appear, or productization transforms an internal tool into a platform.

**Exit condition:** None — this stage remains active for as long as the project continues evolving under doctrinal governance.

---

## Feature Path (Features)

For new capabilities being added to existing systems.

### Stage 0 — Raw Feature Request

A feature need is expressed. It may be:
- a user request for new functionality
- a product decision to expand capability
- an integration requirement
- a workflow improvement

**What the AI must do:**
- recognize this as a Feature (not a new project)
- identify the existing system it belongs to
- select the Feature Path

**Exit condition:** The AI has enough context to begin feature discovery.

### Stage 1 — Context Discovery

The AI discovers both the existing system context and the feature needs.

**This combines:**
- **Brownfield discovery** — understanding the existing system's architecture, conventions, constraints, and integration points (see `15_BROWNFIELD_DISCOVERY_PROTOCOL.md`)
- **Feature discovery** — understanding what the feature must do, who uses it, how it fits into existing flows, and what it must not break

Discovery must be proportional: enough to understand the feature and its impact, not a full project re-discovery.

**Exit condition:** The AI understands both the existing system context and the feature requirements sufficiently to consolidate.

### Stage 2 — Feature Consolidation

The AI transforms discovery into a coherent feature understanding:
- what the feature is
- how it fits into the existing system
- what it must not break
- what constraints the existing system imposes
- what the implementation implications are

**Exit condition:** The feature can be expressed as a coherent candidate for a Feature Specification.

### Stage 3 — Feature Specification (Lightweight Agreement)

A lightweight agreement that defines:
- what the feature is
- what it is not
- how it integrates with the existing system
- what it must not break
- what has been confirmed
- what remains open

This is lighter than a full Work Agreement but still formal enough to prevent undefined features from entering implementation.

**Exit condition:** The Feature Specification exists and is coherent enough to evaluate.

### Stage 4 — Implementation Readiness

The AI verifies whether the feature is ready to implement:
- the feature scope is clear
- the integration points are understood
- the constraints are known
- critical unknowns are resolved
- the existing system's conventions are understood

**Exit condition:** Implementation readiness is explicitly granted.

### Stage 5 — Feature Delivery

The AI delivers the feature implementation:
- code
- tests
- integration
- documentation

Delivery must respect the existing system's architecture, conventions, and constraints.

**Execution flow applies:** ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR (see `07_DELIVERY_PROTOCOL.md`). Depth is proportional — enough to execute with mastery, not a full project-level execution.

**Rigid Payload required:** Output must include Diagnóstico, Alterações, Enforcement, Rollback (see `09_OUTPUT_QUALITY_STANDARD.md`).

**100% criterion:** Compiles + tests pass + no tech debt + meets spec + no broken dependencies (see `09_OUTPUT_QUALITY_STANDARD.md`).

**Validators:** type-check, lint, test, security-scan, contract-check, tech-debt-check, impact-analysis (see `20_ENFORCEMENT_LAYER.md`).

**Exit condition:** The feature is implemented and verified at 100%.

### Stage 6 — Evolution

The feature may evolve. Changes must be governed to prevent drift from the original specification and the existing system's integrity.

---

## Change Path (Refactoring)

For structural improvements to existing code without changing behavior.

### Stage 0 — Raw Change Request

A refactoring or structural improvement need is expressed. It may be:
- code that has become hard to maintain
- a design pattern that needs to be applied
- a structural debt that needs to be paid
- a preparation for future features

**What the AI must do:**
- recognize this as a Refactoring
- identify the codebase area affected
- select the Change Path

**Exit condition:** The AI has enough context to begin codebase analysis.

### Stage 1 — Codebase Analysis

The AI analyzes the current state of the code:
- current structure and architecture
- dependencies and coupling
- code patterns and conventions
- test coverage
- areas of risk

This is brownfield discovery focused on understanding what exists and why it is the way it is.

See `15_BROWNFIELD_DISCOVERY_PROTOCOL.md` for the analysis framework.

**Exit condition:** The AI understands the current structure and the forces that shaped it.

### Stage 2 — Impact Analysis

The AI analyzes what the change would affect:
- what modules are impacted
- what dependencies change
- what tests need to change
- what behavior must be preserved
- what risks exist
- what the migration path looks like

**Exit condition:** The impact is understood and the change can be planned.

### Stage 3 — Change Plan

A formal plan that defines:
- what will change
- what will stay the same
- what behavior must be preserved
- what the steps are
- what the risks are
- how the change will be verified

**Exit condition:** The Change Plan exists and is coherent enough to evaluate.

### Stage 4 — Change Readiness

The AI verifies whether the change is ready to execute:
- the current state is understood
- the impact is mapped
- the plan is sound
- the verification approach is defined
- critical risks are addressed

**Exit condition:** Change readiness is explicitly granted.

### Stage 5 — Change Delivery

The AI executes the change:
- refactored code
- updated tests
- migration (if needed)
- documentation updates

Delivery must preserve behavior exactly. Any behavior change must be explicit and justified.

**Execution flow applies:** ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR (see `07_DELIVERY_PROTOCOL.md`). ESTUDAR is especially critical here — understanding why the code is the way it is before changing it.

**Rigid Payload required:** Output must include Diagnóstico, Alterações, Enforcement, Rollback (see `09_OUTPUT_QUALITY_STANDARD.md`).

**100% criterion:** Identical behavior (proof of equivalence) + cleaner code + no regression (see `09_OUTPUT_QUALITY_STANDARD.md`).

**Validators:** type-check, lint, test, property-tests, mutation-test (see `20_ENFORCEMENT_LAYER.md`). Mutation testing is especially critical for refactoring — it verifies tests actually detect behavioral changes.

**Exit condition:** The change is executed and verified at 100%.

### Stage 6 — Evolution

The refactored code may evolve. Changes must be governed to prevent new debt.

---

## Fix Path (Bugfixes)

For corrections of incorrect behavior in existing code.

### Stage 0 — Bug Report

A bug is reported. It may be:
- an error message
- unexpected behavior
- a crash
- a performance issue
- a data corruption problem

**What the AI must do:**
- recognize this as a Bugfix
- assess severity (critical, important, minor)
- select the Fix Path

**Exit condition:** The AI has enough information to begin problem discovery.

### Stage 1 — Problem Discovery

The AI discovers the nature of the bug:
- what is the expected behavior?
- what is the actual behavior?
- how can it be reproduced?
- when did it start?
- what conditions trigger it?
- what is the scope of impact?

**Exit condition:** The bug is understood and reproducible (or as reproducible as possible).

### Stage 2 — Root Cause Analysis

The AI traces the symptom to its root cause:
- where in the code does the problem originate?
- what is the actual defect?
- is it a logic error, a design error, a configuration error, or a data error?
- is it a local fix or does it require structural change?

**Exit condition:** The root cause is identified and understood.

### Stage 3 — Fix Plan

A plan that defines:
- what the fix is
- why it addresses the root cause (not just the symptom)
- what it must not break
- how it will be verified
- whether it needs a structural fix or a local fix

**Exit condition:** The Fix Plan exists and is ready to execute.

### Stage 4 — Fix Delivery

The AI executes the fix:
- corrected code
- regression tests
- verification

Delivery must address the root cause, not just the symptom. Symptom-only fixes are a doctrinal failure.

**Execution flow applies:** ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR (see `07_DELIVERY_PROTOCOL.md`). ESTUDAR is especially critical here — root cause analysis is the core of bugfix work.

**Rigid Payload required:** Output must include Diagnóstico, Alterações, Enforcement, Rollback (see `09_OUTPUT_QUALITY_STANDARD.md`).

**100% criterion:** Root cause resolved + bug test passes + no new bugs (see `09_OUTPUT_QUALITY_STANDARD.md`).

**Validators:** type-check, lint, test, security-scan (see `20_ENFORCEMENT_LAYER.md`).

**Exit condition:** The fix is implemented and ready for verification.

### Stage 5 — Verification

The AI verifies that:
- the original bug is fixed
- no new bugs are introduced
- the fix addresses the root cause
- regression tests pass

**Exit condition:** The fix is verified and the bug is closed.

---

## Light Path (Small Tasks)

For small implementation work items: scripts, configurations, integrations, minor changes.

### Stage 0 — Task Request

A small task is requested. It may be:
- a utility script
- a configuration change
- a minor integration
- a small code change
- a data transformation

**What the AI must do:**
- recognize this as a Task (not a project)
- assess whether it is truly small or if it needs a heavier path
- select the Light Path

**Exit condition:** The AI has enough context to begin task discovery.

### Stage 1 — Task Discovery

Quick, focused discovery:
- what exactly is needed?
- what are the constraints?
- what are the success criteria?
- are there any hidden complexities?

Discovery here is lightweight but not skipped. Even small tasks need a moment of understanding.

**Exit condition:** The task is understood well enough to brief.

### Stage 2 — Task Brief

A minimal agreement:
- what to do
- what constraints apply
- what success looks like
- what to watch out for

**Exit condition:** The Task Brief is clear enough to execute.

### Stage 3 — Task Delivery

The AI executes the task:
- implementation
- verification
- delivery

Delivery must be correct, complete, and verified. Even small tasks deserve quality.

**Execution flow applies (abbreviated):** ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR (see `07_DELIVERY_PROTOCOL.md`). Each stage is lightweight but not skipped. Even small tasks need a moment of understanding before execution.

**Rigid Payload required (abbreviated):** Output must include Diagnóstico, Alterações, Enforcement, Rollback — each can be brief (see `09_OUTPUT_QUALITY_STANDARD.md`).

**100% criterion:** Compiles + tests pass + no tech debt + meets spec + no broken dependencies (see `09_OUTPUT_QUALITY_STANDARD.md`).

**Validators:** type-check, lint (see `20_ENFORCEMENT_LAYER.md`).

**Exit condition:** The task is delivered and verified at 100%.

---

## Direct Path (Questions)

For informational, analytical, or advisory requests with no implementation.

### Stage 0 — Question

A question is asked. It may be:
- a technical question
- an architectural opinion
- an analysis request
- an explanation request
- a recommendation request

**What the AI must do:**
- recognize this as a Question
- select the Direct Path

### Stage 1 — Direct Response

The AI responds directly, but with discipline:
- understand the question fully before answering
- distinguish fact from opinion
- make assumptions explicit
- provide a structured, useful answer
- note any important caveats

Even in direct response mode, the doctrine's principles apply:
- no hidden assumptions
- no false certainty
- no performance theater
- transparent truthfulness

**100% criterion:** Exact + no irrelevance + no critical omission + semantically precise (see `09_OUTPUT_QUALITY_STANDARD.md`).

**No execution flow:** The 5-stage execution flow does not apply — there is no implementation.

**No Rigid Payload:** The Rigid Payload format does not apply — there is no code to document.

**No validators:** No validators apply — there is no code to verify (see `20_ENFORCEMENT_LAYER.md`).

**Exit condition:** The question is answered at 100%.

---

## Lifecycle Integrity Rules

The lifecycle only works if the following rules are respected.

### Rule 1 — Stages Are Logically Sequential
Within each path, stages are sequential in logic, even when some transitions happen quickly.

### Rule 2 — Earlier Stage Work Must Exist Before Later Stage Legitimacy
A later stage is only valid if the relevant work of the earlier stage actually exists.

### Rule 3 — Fast Progression Is Allowed, Silent Skipping Is Not
The doctrine allows acceleration, but not hidden omission. Even in the Light Path, discovery must happen — it is just faster.

### Rule 4 — Delivery Without Readiness Is a Failure
If delivery begins without the appropriate readiness verification for the chosen path, the lifecycle has been violated.

### Rule 5 — Work Can Re-Enter Earlier Stages
When scope or context materially changes, the work may need renewed discovery, consolidation, or agreement revision.

### Rule 6 — Work Initiation Is a Threshold, Not a Mood
Work becomes formally initiated through agreement, not through enthusiasm.

### Rule 7 — Proportionality Is Mandatory
The depth of process must match the complexity of work. Over-engineering small tasks is a doctrinal failure. Under-engineering large tasks is a doctrinal failure. The AI must classify correctly and apply the appropriate path.

### Rule 8 — Classification Can Be Revised
If, during any stage, the AI discovers that the work is more complex or different than initially classified, it must re-classify and switch to the appropriate path. Silent path continuation when the work type has changed is a doctrinal failure.

---

## Lifecycle Summary Table

### Full Lifecycle (Projects)

| Stage | Name | Main Purpose | Build Allowed? |
|------|------|--------------|----------------|
| 0 | Raw Work Impulse | Surface the initial idea, pain, or ambition | No |
| 1 | Guided Discovery | Reveal project dimensions through structured clarification | No |
| 2 | Deterministic Consolidation | Transform discovery into coherent understanding | No |
| 3 | Work Agreement (Full) | Formally define the project as an engineering identity | No |
| 4 | Build Readiness Verification | Explicitly judge whether construction may begin | Only if approved |
| 5 | Structured Delivery Initiation | Begin serious architecture and build-relevant output | Yes |
| 6 | Governed Evolution | Preserve coherence as the project grows and changes | Yes, under governance |

### Feature Path

| Stage | Name | Main Purpose | Implementation Allowed? |
|------|------|--------------|--------------------------|
| 0 | Raw Feature Request | Surface the feature need | No |
| 1 | Context Discovery | Understand existing system + feature needs | No |
| 2 | Feature Consolidation | Organize understanding into feature meaning | No |
| 3 | Feature Specification | Confirm the feature scope and integration | No |
| 4 | Implementation Readiness | Verify readiness to implement | Only if approved |
| 5 | Feature Delivery | Implement the feature | Yes |
| 6 | Evolution | Govern feature changes | Yes, under governance |

### Change Path (Refactoring)

| Stage | Name | Main Purpose | Change Allowed? |
|------|------|--------------|------------------|
| 0 | Raw Change Request | Surface the refactoring need | No |
| 1 | Codebase Analysis | Understand current structure | No |
| 2 | Impact Analysis | Map what the change affects | No |
| 3 | Change Plan | Define the change formally | No |
| 4 | Change Readiness | Verify readiness to change | Only if approved |
| 5 | Change Delivery | Execute the change | Yes |
| 6 | Evolution | Govern subsequent changes | Yes, under governance |

### Fix Path (Bugfixes)

| Stage | Name | Main Purpose | Fix Allowed? |
|------|------|--------------|---------------|
| 0 | Bug Report | Surface the bug | No |
| 1 | Problem Discovery | Understand and reproduce the bug | No |
| 2 | Root Cause Analysis | Trace symptom to origin | No |
| 3 | Fix Plan | Define the fix formally | No |
| 4 | Fix Delivery | Execute the fix | Yes |
| 5 | Verification | Verify fix is correct, no regressions, root cause addressed | Yes |

### Light Path (Small Tasks)

| Stage | Name | Main Purpose | Execution Allowed? |
|------|------|--------------|---------------------|
| 0 | Task Request | Surface the task | No |
| 1 | Task Discovery | Quick focused understanding | No |
| 2 | Task Brief | Minimal agreement | No |
| 3 | Task Delivery | Execute and verify | Yes |

### Direct Path (Questions)

| Stage | Name | Main Purpose | Response Allowed? |
|------|------|--------------|---------------------|
| 0 | Question | Receive the question | No |
| 1 | Direct Response | Answer with discipline | Yes |

---

## Lifecycle Success Condition

The lifecycle is functioning correctly when:
- work is classified correctly before process begins
- the appropriate path is selected for the work type
- process depth is proportional to work complexity
- raw ideas are not mistaken for build-ready work
- discovery is guided rather than improvised
- consolidation creates real structural understanding
- work is formally agreed before execution
- readiness is judged explicitly (where applicable)
- delivery begins only after appropriate readiness
- later evolution does not silently corrupt original work logic
- small tasks are not over-engineered
- large tasks are not under-served

That is the official lifecycle success condition.

---

## Protocol Coverage Note

Dedicated protocol files exist for the full lifecycle's stages 1–5 (discovery, consolidation, readiness, delivery). The other paths use adapted versions of these protocols, scaled by proportionality.

- **Stage 0** (Raw Work Impulse) is a pre-doctrinal state — the impulse exists before the AI engages. The doctrine begins acting at classification.
- **Stage 6** (Governed Evolution) is governed by the doctrine's governance layer (`17_VERSIONING_POLICY.md`, `18_EVOLUTION_LOG.md`, `19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md`) rather than by a single protocol file. Evolution is inherently cross-cutting and is governed by these instruments collectively.

For task classification, see `11_TASK_CLASSIFICATION_GUIDE.md`.
For brownfield discovery (existing systems), see `15_BROWNFIELD_DISCOVERY_PROTOCOL.md`.

---

## Operational State Interaction with Lifecycle Paths

The lifecycle paths defined above determine the **sequence of stages** for each work type. The **Operational State** (see `21_OPERATIONAL_STATES.md`) determines **how strict the rules are** within each stage.

The Operational State is orthogonal to the lifecycle path — it applies across all paths:

| | Exploratory | Formative | Stable |
|---|---|---|---|
| Discovery depth | Minimal | Light | Standard (per path) |
| Consolidation | Not required | Continuous (squash freely) | Formal |
| Agreement | Not required | Light (Task Brief) | Standard (per path) |
| Readiness check | Not required | Light | Standard |
| Rigid Payload | No | Only on committed changes | Yes |
| 100% criterion | N/A (throwaway) | "100% of current understanding" | Full 100% |
| Migrations | N/A | Squash freely | Ordered, reversible |
| Traceability | None | Only final state | Full |
| Mega-tech protocols | Skipped | Lighter (on commit) | Full (all 12 — see files 23-34) |

### Per-Item State Within a Project

A project following the Full Lifecycle may have different work items in different states:
- The core architecture may be in **Stable** (frozen, tested, full process)
- A new feature being added may be in **Formative** (iterating, migrations squashable)
- A spike for a future capability may be in **Exploratory** (throwaway)

The lifecycle path applies to the work type. The Operational State applies to the specific work item. Both must be determined before work begins.

### The Consolidation Moment

When work transitions from Formative to Stable, the Consolidation Moment must be performed (see `21_OPERATIONAL_STATES.md`). This is a deliberate ritual — not a gradual drift:
1. Squash migrations
2. Remove workarounds
3. Remove debug/experimental code
4. Clean architecture
5. Freeze API surface
6. Write tests
7. Document final state
8. Declare Stable explicitly

---

## Next File

Continue to:

`04_DISCOVERY_PROTOCOL.md`
