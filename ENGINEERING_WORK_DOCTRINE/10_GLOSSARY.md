# GLOSSARY

## Purpose of This File

This file defines the official vocabulary of the Engineering Work Doctrine.

Its purpose is to stabilize meaning.

A doctrine loses power when its core terms drift over time, become overloaded, or start being used loosely across different stages and documents.

This glossary exists to ensure that the doctrine preserves:
- semantic precision
- internal coherence
- cross-document consistency
- stable operational interpretation
- controlled growth of meaning

All core doctrinal terms must be interpreted according to this glossary unless a later version explicitly revises them.

---

## 0-9

### 100% as Floor
The principle that 100% is the minimum acceptance criterion, not the ceiling. Below 100%, work is not done. The definition of 100% varies by work type and Operational State. See `02_OPERATIONAL_PRINCIPLES.md` (Principle 2), `09_OUTPUT_QUALITY_STANDARD.md`, `20_ENFORCEMENT_LAYER.md`, `21_OPERATIONAL_STATES.md`.

---

## A

### Accessible Discovery
A discovery approach that does not require the user to possess technical vocabulary, architectural training, systems language, or engineering fluency in order to answer meaningfully.

Accessible discovery translates structural complexity into low-friction, user-answerable decision structures.

It is a required quality of doctrine-compliant discovery.

---

### Actor
Any person, role, system, or operational participant that interacts with, depends on, administers, observes, influences, or is governed by the project.

Actors may include:
- end users
- operators
- managers
- admins
- approvers
- external systems
- service accounts
- automated agents

The doctrine uses “actor” as a structural term, not merely as a UI user label.

---

### Actor Logic
The structured understanding of who interacts with the project and in what capacity.

Actor logic includes:
- types of actors
- responsibilities
- interaction boundaries
- visibility differences
- control distinctions
- possible permission implications

Actor logic is often a decisive factor in readiness and architectural seriousness.

---

### Architectural Implication
A structural consequence that follows logically from the discovered and consolidated nature of the project, even before full architecture is formally delivered.

Examples:
- need for role-based access
- need for auditable history
- need for environment separation
- need for offline synchronization logic
- need for multi-unit partitioning

Architectural implications are not yet full architecture, but they are structurally meaningful consequences.

---

### Assumption
A provisional judgment made by the AI in the absence of full confirmation.

Under the doctrine, assumptions are allowed only when:
- they are structurally safe enough
- they do not distort core project identity
- they are made transparently
- they remain revisable without causing hidden architectural harm

Assumptions must never be hidden as fact.

---

### Auditability
The ability of the project to preserve and expose traceable records of relevant actions, states, decisions, changes, or events.

Auditability may include:
- who did what
- when it happened
- what changed
- what was approved
- what was reversed
- what is immutable or historically preserved

The doctrine treats auditability as a structural consideration, not merely a reporting convenience.

---

### ADR (Architecture Decision Record)
A durable record of a significant architectural decision, including context, alternatives considered, the decision, and consequences. ADRs ensure that the rationale for decisions survives beyond the moment of decision. See `24_ARCHITECTURE_DECISION_RECORDS.md`.

---

### API Governance Protocol
The doctrinal protocol for API design, versioning, error handling, pagination, and consistency. Ensures APIs within a system follow the same conventions. See `32_API_GOVERNANCE_PROTOCOL.md`.

---

## B

### Birth
**Deprecated.** See "Work Initiation" instead.

The term "birth" was used in earlier versions of the doctrine to refer to the formal start of a project. The doctrine now governs all engineering work, not just new projects, and uses "initiation" as the general term.

---

### Brownfield
Work that involves modifying, fixing, or improving an existing system, as opposed to creating something new (greenfield).

Brownfield work requires understanding the existing system's architecture, conventions, constraints, and integration points before making changes. See `15_BROWNFIELD_DISCOVERY_PROTOCOL.md`.

---

### Brownfield Discovery
The process of understanding an existing system's structure, conventions, constraints, and integration points before making changes to it.

Brownfield discovery is the counterpart to greenfield discovery. Its depth scales with the work type — full context analysis for refactoring, focused discovery for bugfixes, quick scan for small tasks. See `15_BROWNFIELD_DISCOVERY_PROTOCOL.md`.

---

### Build Legitimacy
The condition under which serious implementation-oriented delivery may begin without violating doctrinal integrity.

Build legitimacy depends on:
- adequate discovery
- successful consolidation
- coherent work agreement
- explicit readiness
- absence of unresolved critical blockers

A project without build legitimacy must not enter serious delivery.

---

### Build Readiness
The formally judged condition in which a project is sufficiently clear, coherent, and governed to allow serious structured delivery to begin.

Build readiness is not enthusiasm, momentum, or emotional confidence.

It is an explicit doctrinal decision.

---

### Build Readiness Gate
The formal evaluative stage that determines whether the project may responsibly enter structured delivery.

The gate exists between consolidation and delivery.

Its purpose is to prevent premature implementation.

---

## C

### Change Path
The lifecycle path used for refactoring — structural improvements to existing code without changing behavior.

The Change Path focuses on codebase analysis, impact analysis, and behavior preservation. See `03_PROJECT_LIFECYCLE.md`.

---

### Characterization Test
A test written to capture the current behavior of code before refactoring, even if that behavior is wrong. Characterization tests are not "good tests" — they are "current behavior tests" used to prove equivalence after refactoring.

Required when refactoring codebases that have no existing tests. See `09_OUTPUT_QUALITY_STANDARD.md` — Refactoring Without Tests protocol.

---

### Confirmed
A truth-status category indicating that a project element is directly supported by clarified user input or by explicitly established project definition.

Confirmed elements may be treated as part of formal project reality, unless later revised.

The doctrine requires that confirmed elements remain distinguishable from inferred, recommended, and open elements.

---

### Confirmed Scope
One of the Four Doctrinal Layers. The subset of project scope that has been explicitly confirmed through discovery and consolidation, distinguishing it from the maximum plausible horizon, the structural foundation needed at birth, and the delivery sequence.

Confirmed scope represents what the project is responsible for delivering now, as opposed to what it might become or what must be structurally acknowledged.

The doctrine requires that confirmed scope remain explicitly distinguishable from the plausible horizon at all stages of project birth and delivery.

See also: Scope, Structural Foundation, Maximum Plausible Horizon, Delivery Sequence.

---

### Consolidation
The doctrine stage in which discovery outputs are transformed into coherent structural understanding.

Consolidation does not merely repeat discovery.

It synthesizes discovery into:
- project identity
- purpose logic
- actor understanding
- operational meaning
- structural implications
- visible lacunae
- contract-ready coherence

Consolidation is the bridge between discovery and formal project birth.

---

### Consolidation Moment
The deliberate ritual that transitions work from Formative to Stable Operational State. Includes: squashing migrations, removing workarounds, removing debug/experimental code, cleaning architecture, freezing API surface, writing tests, documenting final state, and declaring Stable explicitly. The Consolidation Moment is mandatory — work does not "drift" into Stable. See `21_OPERATIONAL_STATES.md`.

---

### Constitution
The project-specific component of a Full Work Agreement that defines non-negotiable invariants, standards, prohibitions, and validation configuration. Each project has its own Constitution. The doctrine is universal; the Constitution is local. See `12_TEMPLATE_WORK_AGREEMENT.md`, `20_ENFORCEMENT_LAYER.md`.

---

### Contract
In doctrine usage, “contract” refers to the formal articulation of project identity, scope logic, structural implications, and governed uncertainty.

It is not limited to a legal meaning.

A project birth contract is the formal artifact that makes the project engineerable as a coherent object.

---

### Contract-Aligned
An output, decision, or delivery is contract-aligned when it remains traceable to the meaning, constraints, scope boundaries, and structural logic established in the Project Birth Contract.

Contract alignment is mandatory for delivery quality.

---

### Critical Blocking Lacuna
A missing definition, clarification, or distinction whose absence prevents responsible project birth or serious delivery.

Critical blocking lacunae affect things such as:
- project identity
- structural class
- actor model
- core operational logic
- major governance needs
- decisive environment assumptions
- readiness legitimacy

Their presence prevents valid progression.

---

## D

### Direct Path
The lifecycle path used for questions — informational, analytical, or advisory requests with no implementation.

In the Direct Path, the AI responds directly but with discipline: understanding the question fully, distinguishing fact from opinion, making assumptions explicit, and providing structured answers. See `03_PROJECT_LIFECYCLE.md`.

---

### Delivery
The doctrine stage in which the AI begins serious build-relevant output after readiness has been explicitly granted.

Delivery may include:
- architecture
- domains
- modules
- data structures
- security posture
- operational sequencing
- implementation artifacts

Delivery is not ideation.  
Delivery is legitimate engineering-oriented direction.

---

### Delivery Legitimacy
The condition in which delivery can proceed without hidden violations of truthfulness, readiness, stage appropriateness, or project identity coherence.

Delivery legitimacy depends on doctrinal compliance, not conversational momentum.

---

### Delivery Mode
A distinct mode of delivery emphasis, such as:
- structural delivery
- data delivery
- flow delivery
- codebase delivery
- execution delivery

Delivery modes allow the doctrine to remain adaptive while preserving stage integrity.

---

### Delivery Sequence
The order in which project parts should be delivered or implemented.

The doctrine distinguishes delivery sequence from scope definition.

Sequence answers “what comes first.”  
Scope answers “what belongs to the project now.”

They must not be confused.

---

### Deterministic Consolidation
Consolidation performed in a way that produces explicit, governable, and structurally coherent project meaning rather than informal or impressionistic synthesis.

Deterministic consolidation is the doctrinal standard.

---

### Deterministic Discovery
A discovery process that reduces ambiguity through guided structure rather than vague questioning.

Deterministic discovery is:
- guided
- low-friction
- accessible
- structurally aware
- synthesis-oriented

It is a defining characteristic of the doctrine.

---

### Doctrinal Integrity
The condition in which project work remains faithful to the doctrine's principles, lifecycle, truth standards, readiness rules, and quality standards.

A process or output may look sophisticated and still violate doctrinal integrity.

Integrity is determined by structural faithfulness, not style.

---

### Deprecation Protocol
The doctrinal protocol for removing or replacing existing functionality. Requires a deprecation plan with: what is deprecated, why, what replaces it, migration path, timeline, consumer impact, backward compatibility period, and communication plan. See `07_DELIVERY_PROTOCOL.md` — Deprecation Protocol.

---

### Discovery Dimension Protocol
The protocol that ensures discovery systematically covers all dimensions that could materially affect the work, regardless of domain. Covers 13 dimension categories: safety/criticality, compliance/regulatory, non-functional requirements, hardware/environmental, ML-specifics, large-scale migration, large-scale legacy, multi-team coordination, security/threat model, observability requirements, data governance landscape, testing strategy requirements, dependency landscape. See `22_DISCOVERY_DIMENSION_PROTOCOL.md`.

---

### Debt Register
A tracked record of all technical debt in a Stable system. Each entry includes: debt ID, description, type, severity, location, owner, payoff plan, status, date incurred, and date paid. See `27_TECHNICAL_DEBT_PROTOCOL.md`.

---

### DORA Metrics
The four key metrics for measuring engineering effectiveness: Deployment Frequency, Lead Time for Changes, Change Failure Rate, and Mean Time to Recovery (MTTR). See `34_METRICS_FEEDBACK_LOOP.md`.

---

### Data Governance Protocol
The doctrinal protocol for data classification, protection, access control, retention, and disposal. Defines 4 classification levels (Public, Internal, Confidential, Restricted) and handling requirements for each. See `33_DATA_GOVERNANCE_PROTOCOL.md`.

---

### Dependency Management Protocol
The doctrinal protocol for evaluating, versioning, updating, and securing third-party dependencies. Defines evaluation criteria, versioning rules, update protocol, and security requirements. See `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`.

---

### Documentation Protocol
The doctrinal protocol for living documentation that survives beyond individual work items. Defines documentation types (architecture, API, runbooks, onboarding), quality standards, and README requirements. See `29_DOCUMENTATION_PROTOCOL.md`.

---

## E

### Enforcement Instrument
Any tool that implements the validator categories, gates, integrity protection, and proportional enforcement defined by the doctrine. The doctrine is enforcement-instrument-agnostic. See `20_ENFORCEMENT_LAYER.md`.

---

### Enforcement Layer
The third layer of the five-layer architecture. Guarantees that executed work is 100% correct through deterministic validators, gates, integrity protection, operational states, and discovery dimensions. See `20_ENFORCEMENT_LAYER.md`.

---

### Exploratory
An Operational State where the output is throwaway. The goal is to learn whether something is viable, not to produce durable artifacts. Process is minimal, workarounds are allowed, no Rigid Payload required, no traceability required. See `21_OPERATIONAL_STATES.md`.

---

### Essence of the Project
The fundamental nature of what the project is.

Project essence answers questions such as:
- What kind of thing is this?
- What is it fundamentally trying to make possible?
- What problem or transformation defines its identity?

Essence is more fundamental than features.

---

### Evolutive Lacuna
A missing definition that naturally belongs to later project evolution and should not block legitimate birth or proportionate delivery.

Examples:
- advanced future automation rules
- later monetization details
- optional future integrations
- mature optimization policies

Evolutive lacunae must be visible, but they do not block progress by default.

---

### Execution Flow
The 5-stage flow (ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR) that defines how work is executed with mastery. Defined in `07_DELIVERY_PROTOCOL.md`.

---

### Explicitness
The quality of making important distinctions visible rather than leaving them hidden or implied.

The doctrine values explicitness in:
- truth status
- scope boundaries
- reservations
- open items
- readiness judgments
- next steps
- structural implications

A polished but implicit output may still be weak.

---

## F

### Formative
An Operational State where the output is being shaped. It matters now, but it will be rewritten or consolidated before becoming durable. The history of intermediate states is not valuable — only the final state is. Consolidation is encouraged (squash migrations, rewrite freely). Workarounds allowed with note. Rigid Payload only on committed changes. See `21_OPERATIONAL_STATES.md`.

---

### Reusable Artifact Layer
The set of reusable templates, manifests, scripts, flows, runtime configurations, birth mechanisms, and evolution mechanisms within the ecosystem that generate or govern new project instances.

When a structural problem is identified at the reusable artifact layer, the correction must be made there rather than patched at the individual project level.

See: `19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md`

---

### Feature Path
The lifecycle path used for features — new capabilities being added to existing systems.

The Feature Path combines brownfield discovery (understanding the existing system) with feature discovery (understanding what the feature must do). It is lighter than the Full Lifecycle but still formal. See `03_PROJECT_LIFECYCLE.md`.

---

### False Positive
A validator report that flags a failure which is not actually a failure — the validator is wrong, the code is correct.

False positives must be investigated, documented, and bypassed explicitly with justification. Silent bypass of false positives is Anti-Pattern 29. See `20_ENFORCEMENT_LAYER.md` — False Positive Protocol.

---

### Fix Path
The lifecycle path used for bugfixes — corrections of incorrect behavior in existing code.

The Fix Path focuses on problem discovery, root cause analysis, and fix verification. It is lighter than the Full Lifecycle and prioritizes root cause over symptom. See `03_PROJECT_LIFECYCLE.md`.

---

### Formal Birth
**Deprecated.** See "Work Initiation" instead.

The state in which work is sufficiently defined, consolidated, and agreed to be treated as a legitimate engineering object.

Work initiation is achieved through doctrinal progression, not by enthusiasm or conversational length.

---

### Four Doctrinal Layers
The four explicit layers that must be distinguished throughout project birth and delivery:

1. **Maximum Plausible Horizon** — the highest structurally plausible future the project could realistically evolve into
2. **Structural Foundation Needed at Birth** — the structural considerations that must be acknowledged at birth to avoid future structural blindness
3. **Confirmed Present Scope** — what has been explicitly confirmed through discovery and consolidation
4. **Delivery Sequence** — the order in which confirmed scope should be delivered

These layers must not be collapsed into each other. Confusing horizon with scope leads to grandiosity inflation; confusing scope with foundation leads to structural blindness.

See also: Maximum Plausible Horizon, Structural Foundation, Confirmed Scope, Delivery Sequence.

---

### Foundation
The base layer of the doctrine containing its philosophical and structural premises.

In the folder structure, this corresponds to documents such as:
- doctrine foundation
- operational principles
- project lifecycle

Foundation explains the doctrine's worldview and basic logic.

---

### Future Horizon
Deprecated shorthand for Maximum Plausible Horizon. Retained for backward interpretation only.

See: Maximum Plausible Horizon.

---

## G

### Greenfield
Work that involves creating something new from scratch, as opposed to modifying an existing system (brownfield).

Greenfield work uses the Full Lifecycle path with full discovery, consolidation, and work agreement. See `04_DISCOVERY_PROTOCOL.md` for the greenfield discovery protocol.

---

### Governed Project Evolution
The doctrine stage in which the project continues growing after birth while preserving structural coherence and doctrinal discipline.

Governed evolution prevents silent drift.

It allows projects to expand while:
- revisiting discovery if necessary
- revisiting consolidation if meaning changes
- reevaluating readiness if delivery assumptions are materially altered

---

### Governance
The set of control, accountability, permission, policy, history, approval, separation, and integrity mechanisms that shape responsible project operation.

Governance may include:
- role control
- approval logic
- audit history
- environment separation
- access constraints
- operational accountability
- irreversible action rules

The doctrine treats governance as a structural dimension, not merely an enterprise add-on.

---

### Guided Decision Architecture
A discovery style in which the AI structures user clarification through decisions rather than relying on unstructured open-ended questioning.

Examples:
- yes/no/maybe/not sure/observation
- bounded option sets
- grouped decision blocks
- scenario-led prompts

This is a key operational pattern of the doctrine.

---

### Guided Discovery
The lifecycle stage in which the AI leads structured clarification of the project in a low-friction, structurally aware manner.

Guided discovery is Stage 1 of the project lifecycle.

---

## H

### Horizon
A shorthand doctrinal term usually referring to the Maximum Plausible Horizon of the project.

Horizon is about what the project could plausibly become if it grows in significance, complexity, or scale.

Horizon awareness is used to avoid structural blindness.

It must not be confused with current scope.

---

## I

### Identity
The formal structural understanding of what the project is.

Project identity includes:
- project class
- project purpose
- project role in reality
- major actor logic
- major operational meaning

Identity is one of the most important elements of doctrinal maturity.

---

### Important Non-Blocking Lacuna
A missing definition that matters, but does not invalidate project birth or bounded delivery.

It must be:
- surfaced
- classified
- acknowledged
- governed visibly

It may remain open while work proceeds, provided it does not corrupt structural legitimacy.

---

### Inferred
A truth-status category indicating that an element was not directly stated by the user, but is strongly suggested by context, discovery outputs, or structural logic.

Inference is allowed under the doctrine only when:
- it is reasonable
- it is visible
- it does not distort the project's core identity
- it remains revisable

---

### Integral Structural Recomposition Principle (PREI)
The governing principle that every relevant change to the ecosystem must be treated as a whole-system structural recomposition, never as a minimal local adaptation.

Its central requirement is that the system must emerge from every important change more coherent than it entered, with all previously validated behavior explicitly preserved.

The internal acronym PREI is retained as the established identifier of this principle.

See: `19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md`

---

### Integrity Preservation
The requirement that outputs and decisions must not damage doctrinal legitimacy even when attempting to accelerate progress.

Integrity preservation means:
- not skipping stages silently
- not hiding uncertainty
- not authorizing build prematurely
- not sacrificing structural seriousness for conversational flow

---

### Incident Response Protocol
The doctrinal protocol for handling production incidents. Defines severity levels (SEV1-4), response phases (detect, triage, mitigate, resolve, post-mortem, corrective action), and blameless post-mortem requirements. See `30_INCIDENT_RESPONSE_PROTOCOL.md`.

### SEV1 (Severity 1 — Critical)
The highest incident severity level. Production is down, data loss is occurring, or a critical security breach is active. All hands respond. Mitigation is the immediate priority. Requires a post-mortem within 24 hours of resolution. See `30_INCIDENT_RESPONSE_PROTOCOL.md`.

### SEV2 (Severity 2 — High)
A major incident with significant impact. Key functionality is broken for many users, or a critical degradation is occurring. Rapid response required. Requires a post-mortem within 48 hours of resolution. See `30_INCIDENT_RESPONSE_PROTOCOL.md`.

### SEV3 (Severity 3 — Medium)
A moderate incident with limited impact. Non-critical functionality is broken, or a minor degradation is occurring. Response during normal business hours. Requires a post-mortem within 1 week of resolution. See `30_INCIDENT_RESPONSE_PROTOCOL.md`.

### SEV4 (Severity 4 — Low)
A minor incident with minimal impact. Cosmetic issues, non-user-facing bugs, or minor degradations. Response is best-effort. Post-mortem is optional but recommended for systemic patterns. See `30_INCIDENT_RESPONSE_PROTOCOL.md`.

---

## L

### Lacuna
A meaningful gap in project understanding.

The doctrine uses “lacuna” as a formal term for structured unknowns.

A lacuna is not simply “something not yet discussed.”  
It is something materially missing that requires classification.

Official lacuna classes:
- critical blocking
- important non-blocking
- evolutive

---

### Lacuna Governance
The doctrine's requirement that meaningful unknowns be surfaced, classified, and carried explicitly rather than being silently ignored.

Lacuna governance is essential for honest readiness and responsible delivery.

---

### Lifecycle
The official sequence of project maturity stages defined by the doctrine.

The lifecycle is:
- Raw Project Impulse
- Guided Discovery
- Deterministic Consolidation
- Project Birth Contract
- Build Readiness Verification
- Structured Delivery Initiation
- Governed Project Evolution

Lifecycle discipline is one of the doctrine's strongest protections.

---

### Light Path
The lifecycle path used for small tasks — scripts, configurations, integrations, minor changes.

The Light Path has 4 stages (Task Request, Task Discovery, Task Brief, Task Delivery) and uses minimal process. Discovery is quick but not skipped. See `03_PROJECT_LIFECYCLE.md`.

---

## M

### Maximum Plausible Horizon
The highest structurally plausible future that the project could realistically evolve into.

This is not fantasy, maximalism, or inflated feature imagination.

It is a seriousness discipline.

The AI must internally visualize the maximum plausible horizon in order to avoid under-structuring the project's birth.

---

### Mega-tech Protocols
The 12 operational protocols (files 23-34) that cover the full mega-tech delivery stack: testing strategy, ADRs, observability, security review, technical debt, dependency management, documentation, incident response, quality gates, API governance, data governance, metrics & feedback loop. These protocols scale with Operational State — mandatory in Stable, lighter in Formative, skipped in Exploratory. Together they form Layer 4 of the five-layer architecture. See `00_START_HERE.md`.

---

### Metrics & Feedback Loop Protocol
The doctrinal protocol for measuring engineering performance and collecting feedback for continuous improvement. Covers DORA metrics (deployment frequency, lead time, change failure rate, MTTR), doctrine compliance metrics, and feedback-driven doctrine evolution. See `34_METRICS_FEEDBACK_LOOP.md`.

---

### Five-Layer Architecture
The structural architecture of the Engineering Work Doctrine: Layer 1 (Governance Cognitive, files 00-19), Layer 2 (Execution Flow, file 07), Layer 3 (Enforcement, files 20-22), Layer 4 (Mega-tech Protocols, files 23-34), Layer 5 (Constitution, component of file 12). Each layer answers a distinct question. See `20_ENFORCEMENT_LAYER.md`.

---

### Multi-Team Coordination Protocol
The doctrinal protocol for coordinating work across multiple teams or AI instances. Includes team ownership map, interface contracts, state sharing, conflict prevention, and multi-AI instance coordination. See `13_PROJECT_SESSION_TEMPLATE.md` — Multi-Team Coordination Protocol.

---

## O

### Open
A truth-status category indicating that an element remains unresolved, underdefined, or insufficiently confirmed.

Open elements must not be disguised as settled.

Open status is not a defect by itself.  
It becomes dangerous only when hidden or misclassified.

---

### Operational State
The third dimension of the doctrine (alongside Work Type and Proportionality). Determines how strict the doctrine's rules are, based on the preciousness and reversibility of the output. Three states: Exploratory (throwaway), Formative (being shaped), Stable (precious, full doctrine). Orthogonal to Work Type. Per-item, not per-project. Default is Stable when unclear. See `21_OPERATIONAL_STATES.md`.

---

### Operational Nature
The functional class or real-world operational type of the project.

Examples:
- internal system
- app
- SaaS product
- workflow tool
- offline environment
- operational dashboard
- control system
- hybrid platform

Operational nature helps determine appropriate discovery, structure, and delivery depth.

---

### Operational Proportionality
The doctrine's requirement that implementation seriousness must be calibrated to the actual confirmed need and current project maturity.

Operational proportionality prevents both:
- shallow simplification
- unjustified overdesign

---

### Output Theater
An output that appears intelligent, strong, strategic, or complete, but lacks true structural usefulness or doctrinal legitimacy.

The doctrine rejects output theater.

---

### Observability Protocol
The doctrinal protocol for ensuring work output in Stable state includes the logs, metrics, traces, alerts, and dashboards needed to operate, debug, and monitor the system. Based on the three pillars: logs, metrics, traces. See `25_OBSERVABILITY_PROTOCOL.md`.

---

## P

### Payload Rígido
The mandatory output format for implementation work, consisting of 4 sections: Diagnóstico (what was the problem and root cause), Alterações (what was changed), Enforcement (how it was verified), Rollback (how to revert). See `20_ENFORCEMENT_LAYER.md`.

---

### Preemption Command
The rule that system-level doctrine rules override any AI suggestion when they conflict. The doctrine takes precedence over the AI's default behavior.

---

### Process Override
A user's explicit decision to skip or accelerate a doctrinal process stage (e.g., "skip discovery, I know what I want"). The AI may comply if the user is informed of the risk, the override is recorded, and the work continues with the override noted. Distinct from Quality Override. See Rule 14.2 in `08_DECISION_RULES.md`.

---

### Project Birth
**Deprecated.** See "Work Initiation" instead.

The process through which a raw idea becomes formally legitimate work under the doctrine.

Work initiation includes:
- classification
- discovery
- consolidation
- agreement formation
- readiness judgment (where applicable)

Initiation occurs before serious delivery.

---

### Project Birth Contract
**Deprecated.** See "Work Agreement" instead.

The formal artifact that defines work as a coherent engineering object, at a depth proportional to the work type.

The Work Agreement is the threshold between understanding and legitimate execution.

---

### Project Essence
A synonym-adjacent term to "essence of the project," emphasizing the fundamental identity and purpose of the initiative.

Where both are used, they should be interpreted consistently.

---

### Prompt Salt
A micro-anchor mechanism that re-injects critical rules into the AI's attention cycle throughout a session. Prevents attention degradation over long contexts. See `20_ENFORCEMENT_LAYER.md`.

---

### Proportional Delivery
Delivery that is serious enough for the work, but not inflated beyond what readiness and confirmed scope justify.

It is one of the doctrine's quality requirements.

---

### Proportionality Principle
The foundational principle that process depth must match work complexity.

Over-engineering small tasks with heavy process is a doctrinal failure. Under-engineering large tasks with trivial process is a doctrinal failure. The correct behavior is to classify the work type first and then apply the appropriate level of process.

This principle enables the doctrine to be universal — applicable to all engineering work — without being rigid (too heavy for small work) or shallow (too light for large work).

See: Principle 1 in `02_OPERATIONAL_PRINCIPLES.md`, `11_TASK_CLASSIFICATION_GUIDE.md`.

---

## Q

### Quality Override
A user's explicit decision to accept less than 100% completion (e.g., "ship it even though tests don't pass"). The AI must refuse to declare the work as 100% complete, state explicitly what is not 100%, label the work as "user-accepted incomplete," and record the quality gap. Distinct from Process Override. See Rule 14.2 in `08_DECISION_RULES.md`.

---

### Quality Gate
A checkpoint that must be passed before work can proceed to the next lifecycle stage. Each gate has criteria, verification method, blocking behavior, and override conditions. See `31_QUALITY_GATES.md`.

---

## R

### Readiness
A shorthand term usually referring to build readiness.

Readiness means the project is sufficiently clarified, consolidated, and governed to allow serious structured delivery without hidden core assumptions.

---

### Readiness Gate
Shorthand for Build Readiness Gate.

See: Build Readiness Gate.

---

### Recommended
A truth-status category indicating that the AI is proposing something as good practice, structural protection, or sensible discipline, even though it is not directly confirmed by the user.

Recommendations must be labeled as such.

They must not be disguised as confirmed requirement.

---

### Re-Entry
The act of returning to an earlier lifecycle stage when project evolution or newly surfaced information invalidates prior maturity assumptions.

Examples:
- return to discovery
- return to consolidation
- return to readiness evaluation

Re-entry is legitimate and sometimes necessary.

---

### Relevance
The quality of being specifically tied to the actual project rather than to generic project commentary.

Doctrine-compliant outputs must be relevant, not merely broadly correct.

---

### Reservation
An explicit statement that certain delivery decisions or progress remain bounded by a known open issue that does not currently block work.

Reservations are especially important in conditionally ready projects.

---

## S

### Stable
An Operational State where the output is precious. Full doctrine applies: 100% as Floor is non-negotiable, Rigid Payload mandatory, no workarounds, nothing modified without trace, migrations ordered and reversible. The transition from Formative to Stable requires the Consolidation Moment. See `21_OPERATIONAL_STATES.md`.

---

### Scope
The confirmed present extent of what the project is responsible for now.

Scope is not:
- the full future horizon
- every plausible feature
- the delivery sequence
- the total dream state of the project

The doctrine requires explicit separation between scope and horizon.

---

### Scope Boundary
The line between:
- what belongs to the current project definition
- and what does not yet belong to it

Scope boundaries are necessary for quality consolidation and responsible delivery.

---

### Stage Appropriateness
The quality of an output or decision fitting the correct lifecycle stage.

An output may be intelligent in isolation and still be poor if it belongs to the wrong stage.

---

### Structural Ambition
The doctrine's requirement that projects be born with high architectural seriousness and future awareness.

Structural ambition must be paired with operational proportionality.

---

### Structural Blindness
The failure to consider plausible future responsibilities, governance, control layers, operational weight, or scale implications at project birth.

The doctrine exists partly to prevent structural blindness.

---

### Structural Clarity
The degree to which the project is intelligible in structural terms.

Structural clarity increases when the project becomes clearer in:
- identity
- flows
- actors
- controls
- data implications
- constraints
- open items
- implementation direction

---

### Structural Foundation
The set of project-level structural considerations that must be acknowledged at birth in order to avoid irresponsible project formation.

Structural foundation sits between:
- plausible horizon
- and present confirmed scope

It answers what must already be respected in the initial project shape.

---

### Structural Implication Summary
A synthesis of the major consequences already implied by the discovered and consolidated nature of the project.

This summary is often part of consolidation.

---

### Structural Legitimacy
The condition in which the project or output is serious enough, coherent enough, and explicitly governed enough to support responsible progression.

Structural legitimacy is a stronger criterion than mere conversational plausibility.

---

### Structural Recomposition
The act of treating a relevant change as requiring a full reassessment and reorganization of the system as a whole, rather than a minimal local patch.

Structural recomposition requires:
- reading the current system as a totality
- explicitly preserving what already works
- identifying what the new requires
- analyzing systemic impact
- redesigning the whole before executing

Structural recomposition is the correct mode for all relevant changes in the ecosystem.

See: Integral Structural Recomposition Principle (PREI)

---

### Structured Delivery
Delivery that is organized, explicit, stage-appropriate, truth-aware, build-relevant, and sequenced.

This is the doctrinal standard for delivery.

---

### Structured Output
Any output that is consciously organized into meaningful, usable layers rather than being presented as loose, blended content.

---

### Structured Usefulness
A quality characteristic of outputs that genuinely help the project progress correctly rather than merely adding content.

---

### Ecosystem
The complete operational environment that encompasses projects, doctrine, reusable artifact mechanisms, runtime configuration, topology, shared contexts, and all systemic components governed under the Engineering Work Doctrine and the Structural Recomposition Principle.

---

### Security Review Protocol
The doctrinal protocol for security review of work output. Defines three review levels: Level 1 (automated scanning), Level 2 (manual review), Level 3 (threat modeling). See `26_SECURITY_REVIEW_PROTOCOL.md`.

---

## T

### Task
A work type classification for small implementation work items: scripts, configurations, integrations, minor changes.

Tasks use the Light Path with 4 stages (Task Request, Task Discovery, Task Brief, Task Delivery). See `03_PROJECT_LIFECYCLE.md`, `11_TASK_CLASSIFICATION_GUIDE.md`.

---

### Task Brief
The lightweight work agreement used for small tasks (Task work type).

A Task Brief defines what to do, constraints, success criteria, and what to watch out for. It is the minimal formal agreement that prevents undefined work from entering execution. See `12_TEMPLATE_WORK_AGREEMENT.md`.

---

### Task Classification
The process of identifying the work type (Project, Feature, Refactoring, Bugfix, Task, Question) and selecting the appropriate lifecycle path.

Task classification is the first action the AI takes after receiving any work request. It determines process depth, lifecycle path, and agreement tier. See `11_TASK_CLASSIFICATION_GUIDE.md`.

---

### Truth Status
The doctrinal classification of project statements into:
- confirmed
- inferred
- recommended
- open

Truth status is one of the doctrine's central clarity mechanisms.

---

### Truthfulness
The discipline of preserving visible truth status and refusing to disguise unknowns, inferences, or recommendations as settled fact.

Truthfulness is a core doctrine requirement.

---

### Team Ownership Map
A maintained record of which team owns which component, module, or service in a multi-team system. Part of the project's Work State File. See `13_PROJECT_SESSION_TEMPLATE.md` — Multi-Team Coordination Protocol.

---

### Testing Strategy Protocol
The doctrinal protocol that defines what constitutes "100% verified" for each work type and operational state. Defines 8 test types (unit, integration, e2e, contract, performance, security, chaos, characterization) and the test pyramid (70/20/10). See `23_TESTING_STRATEGY_PROTOCOL.md`.

---

### Technical Debt Protocol
The doctrinal protocol for tracking, classifying, and paying off technical debt. Defines 7 debt types, intentional vs unintentional debt, the Debt Register, and severity classification. See `27_TECHNICAL_DEBT_PROTOCOL.md`.

---

## U

### Uncertainty
Anything not fully settled within the current project understanding.

The doctrine does not attempt to erase uncertainty.
It attempts to classify, govern, and contain it.

---

### Universality of Method
The doctrine's ability to apply across many project types using the same birth logic.

This does not imply generic results.

The doctrine is universal in process, not in project identity.

---

## V

### Validators
Deterministic checks that verify work output meets quality standards. Organized in 3 gates: pre-commit (8 validators), pre-push (6 validators), CI (1 validator). Applied proportionally by work type. See `20_ENFORCEMENT_LAYER.md`.

---

### Visible Uncertainty
Uncertainty that has been surfaced explicitly rather than hidden inside confident language.

The doctrine prefers visible uncertainty over false precision.

---

## W

### Work
Any engineering task that the AI is asked to perform under the doctrine.

Work is the general concept that encompasses all specific work types: projects, features, refactoring, bugfixes, small tasks, and questions. The doctrine governs all work through classification and proportional process.

---

### Work Agreement
The formal artifact that defines work as a coherent engineering object, at a depth proportional to the work type.

The Work Agreement replaces the earlier "Project Birth Contract" and comes in multiple tiers:
- Full Work Agreement (for projects)
- Feature Specification (for features)
- Change Plan (for refactoring)
- Fix Plan (for bugfixes)
- Task Brief (for small tasks)
- Direct (for questions — no formal agreement)

See: `12_TEMPLATE_WORK_AGREEMENT.md`.

---

### Work Initiation
The process through which a raw work request becomes formally legitimate under the doctrine.

Work initiation includes:
- task classification
- discovery (at appropriate depth)
- consolidation (at appropriate depth)
- agreement formation (at appropriate depth)
- readiness judgment (where applicable)

Initiation occurs before serious delivery. Replaces the earlier term "Project Birth."

---

### Work State File
A persistent file that records the doctrinal state of a work item across sessions. Contains: work identity, classification, current lifecycle stage, completed stages, open items, constitution, session log, and next steps.

Required for any work that spans multiple sessions. Ensures state continuity across AI instances and time gaps. See `13_PROJECT_SESSION_TEMPLATE.md` — State Persistence Between Sessions.

---

### Work Type
The classification category assigned to a work request during task classification.

The doctrine recognizes six work types: Project, Feature, Refactoring, Bugfix, Task, Question. Each work type maps to a specific lifecycle path and agreement tier. See `11_TASK_CLASSIFICATION_GUIDE.md`.

---

## Z

### Zero-Downtime Deployment
A deployment strategy that maintains system availability during deployment. Requires health checks, monitoring, automatic rollback on failure, and backward-compatible data migrations. See `20_ENFORCEMENT_LAYER.md` — Rollback section.

---

## Next File

Continue to:

`11_TASK_CLASSIFICATION_GUIDE.md`