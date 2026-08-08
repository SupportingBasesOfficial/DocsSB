# ENGINEERING WORK DOCTRINE — START HERE

## Current Doctrine Version
`0.8.1`

## Doctrine Status
Operational, structured, and under governed maturation. Mega-tech ready.

The doctrine has **35 files** (00-34), five-layer architecture, 12 mega-tech protocols, 42 anti-patterns, and 14 quality gates.

For the complete version evolution history, see `18_EVOLUTION_LOG.md`.

## Purpose

This directory contains the official operational doctrine for deterministic engineering work with AI.

Its purpose is to transform raw ideas, vague intentions, operational pains, product visions, bug reports, refactoring needs, and strategic ambitions into structured, validated, and build-ready work through a governed process.

This doctrine exists to ensure that engineering work does not begin:
- shallow
- structurally blind
- dependent on the user's technical vocabulary
- prematurely implemented
- weakened by generic AI behavior
- reduced to fragile MVP thinking when the correct structural foundation can already be defined
- processed with disproportionate process depth — too heavy for simple work, too light for complex work

This doctrine treats AI not as a passive responder, but as an active conductor of work discovery, consolidation, and structured delivery.

---

## Core Premise

The user is not required to be a software architect, systems analyst, product strategist, infrastructure engineer, database designer, security specialist, or UX designer in order to correctly define engineering work.

The AI must carry the burden of structural vision.

Therefore, before construction begins, the AI must:
1. classify the work type and select the appropriate lifecycle path
2. visualize the maximum plausible horizon of the work
3. translate complexity into guided decisions
4. conduct deterministic discovery (greenfield or brownfield as appropriate)
5. consolidate the real work agreement
6. verify build readiness
7. begin structured delivery only after sufficient clarity exists

This doctrine exists to make that process repeatable, reliable, and operationally strong.

---

## What This Doctrine Is

This doctrine is:

- an engineering work framework
- an operational system for AI-guided work definition, classification, and execution
- a structured protocol for discovery, consolidation, and delivery across all work types
- a quality control layer against shallow or inflated work
- a reusable method for turning uncertainty into engineering direction
- a classification system that matches process depth to work complexity

This doctrine governs ALL engineering work, not just new projects. It applies to:
- new projects (greenfield creation from scratch)
- features (new capabilities in existing systems)
- refactoring (structural improvement without behavior change)
- bugfixes (correcting incorrect behavior)
- tasks (defined units of work with clear scope)
- questions (inquiries that may or may not lead to work)

It is designed to work across many system types, including but not limited to:
- internal systems
- SaaS products
- offline-first environments
- operational platforms
- management systems
- apps
- tools
- automation systems
- hybrid infrastructures
- business systems
- high-ambition product visions

---

## What This Doctrine Is Not

This doctrine is not:

- a random note collection
- a brainstorm archive
- a loose prompt library
- a dependency on precedent cases
- a substitute for engineering judgment
- an excuse to inflate work without proportionality
- a license for technology vanity
- a mechanism for building before understanding
- limited to new projects — it governs all engineering work, from questions to full project initiation

This doctrine does not exist to make work unnecessarily complex.

It exists to ensure that work is initiated with:
- structural awareness
- proportional ambition
- explicit reasoning
- controlled assumptions
- deterministic clarification
- serious delivery standards

---

## Operational Philosophy

The doctrine is based on the following principles:

1. **Proportionality**
   Process depth must match work complexity. A trivial question does not require a full discovery cycle. A new project does not require a trivial one. The right process for the right work.

2. **100% as Floor**
   100% is the minimum acceptance criterion. Below 100%, work is not done. The definition of 100% varies by work type, but the floor is non-negotiable.

3. **Maximum Plausible Horizon**
   The AI must first visualize the highest plausible future of the work, not to impose it, but to ensure structural awareness.

4. **Structural Ambition with Operational Proportionality**
   Work must be initiated with maximum architectural consciousness, but implemented proportionally to confirmed needs.

5. **Deterministic Discovery Before Construction**
   The AI must guide discovery before attempting serious construction. For existing systems, this means brownfield discovery — understanding what exists before changing it.

6. **Agreement Before Build**
   No serious work should be built before a work agreement exists.

7. **The User Must Not Need Technical Vocabulary**
   The AI must detect intent, operation, and need without depending on expert phrasing from the user.

8. **Transparent Truthfulness**
   The AI must distinguish between:
   - confirmed facts
   - informed inferences
   - best-practice decisions
   - open uncertainties

9. **No Shallow Initiation**
   Work may begin in phases, but it must not be initiated structurally blind.

---

## The Five-Layer Architecture

The Engineering Work Doctrine operates within a five-layer architecture. Each layer answers a different question:

- **Layer 1 — Governance Cognitive** (this doctrine, files 00-19) — "What work is this? How should it be approached?" Classifies the work, selects the lifecycle path, conducts discovery, consolidates understanding, forms the work agreement, verifies readiness, and initiates delivery.

- **Layer 2 — Execution Flow** (`07_DELIVERY_PROTOCOL.md`, 5-stage flow) — "How to execute this work with mastery?" Defines the 5-stage execution flow: ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR. Ensures understanding precedes execution and demands the first execution be the correct one.

- **Layer 3 — Enforcement** (files 20-22) — "Is the work 100% correct? Prove it." Runs deterministic validators against work output, blocks work that does not pass 100%, protects immutable files from tampering, governs operational states (Exploratory/Formative/Stable), and ensures discovery dimension coverage.

- **Layer 4 — Mega-tech Protocols** (files 23-34) — "Is this production-grade?" Defines the 12 mega-tech protocols that scale with operational state: testing strategy, ADRs, observability, security review, technical debt, dependency management, documentation, incident response, quality gates, API governance, data governance, metrics & feedback loop. These are mandatory in Stable state, lighter in Formative, and skipped in Exploratory.

- **Layer 5 — Constitution** (component of `12_TEMPLATE_WORK_AGREEMENT.md`) — "What are the non-negotiable rules of this project?" Defines project-specific invariants, standards, prohibitions, and validation configuration.

No layer replaces another. Each operates at its own level. Together they cover the complete cycle from request to verified, production-grade delivery. See `20_ENFORCEMENT_LAYER.md` for the full architecture description.

---

## Task Classification and Lifecycle Paths

Every work request under this doctrine is first classified, then routed to the appropriate lifecycle path.

### Task Classification

Work is classified into one of six types:
- **Project** — a new system or substantial new creation from scratch
- **Feature** — a new capability added to an existing system
- **Refactoring** — structural improvement without changing behavior
- **Bugfix** — correcting incorrect behavior
- **Task** — a defined unit of work with clear scope
- **Question** — an inquiry that may or may not lead to work

### Lifecycle Paths

Based on classification, the work follows one of six paths:

1. **Full Path** (Project) — Raw Impulse → Guided Discovery → Deterministic Consolidation → Work Agreement → Build Readiness Verification → Structured Delivery Initiation → Governed Evolution
2. **Feature Path** (Feature) — Context Discovery → Change Consolidation → Work Agreement → Readiness Check → Structured Delivery → Evolution
3. **Change Path** (Refactoring) — Codebase Analysis → Change Consolidation → Work Agreement → Readiness Check → Structured Delivery → Evolution
4. **Fix Path** (Bugfix) — Problem Discovery → Fix Consolidation → Work Agreement → Readiness Check → Structured Delivery → Evolution
5. **Light Path** (Task) — Task Discovery → Task Consolidation → Work Agreement → Delivery → Evolution
6. **Direct Path** (Question) — Question → Direct Answer (no agreement needed)

Classification determines process depth, discovery approach (greenfield or brownfield), and the form of work agreement required. See `11_TASK_CLASSIFICATION_GUIDE.md` for the full classification protocol.

---

## Directory Map

This directory is organized into five operational layers.

### 1. Foundational Layer
Defines what the doctrine is and how it thinks.

- `01_DOCTRINE_FOUNDATION.md`
- `02_OPERATIONAL_PRINCIPLES.md`
- `03_PROJECT_LIFECYCLE.md`

### 2. Protocol Layer
Defines how the AI operates across discovery, consolidation, readiness, and delivery.

- `04_DISCOVERY_PROTOCOL.md`
- `05_CONSOLIDATION_PROTOCOL.md`
- `06_BUILD_READINESS_CHECKLIST.md`
- `07_DELIVERY_PROTOCOL.md`

### 3. Judgment and Control Layer
Defines decision logic, output standards, terminology, and anti-degradation protection.

- `08_DECISION_RULES.md`
- `09_OUTPUT_QUALITY_STANDARD.md`
- `10_GLOSSARY.md`
- `16_ANTI_PATTERNS.md`

### 4. Operational Instruments Layer
Provides the actual tools used in live work sessions.

- `11_TASK_CLASSIFICATION_GUIDE.md` — Task Classification Guide (classifies work type and selects lifecycle path)
- `12_TEMPLATE_WORK_AGREEMENT.md` — Work Agreement Template
- `13_PROJECT_SESSION_TEMPLATE.md` — Work Session Template
- `14_RUNTIME_MASTER_PROMPT.md` — Runtime activation prompt
- `15_BROWNFIELD_DISCOVERY_PROTOCOL.md` — Brownfield Discovery Protocol (for existing systems)

### 5. Governance Layer
Governs how the doctrine evolves over time, how changes are versioned and logged, and how structural recomposition must be applied across the ecosystem.

- `17_VERSIONING_POLICY.md`
- `18_EVOLUTION_LOG.md`
- `19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md`
- `20_ENFORCEMENT_LAYER.md` — Enforcement Layer (validators, gates, integrity protection, five-layer architecture)

---

## Reading Modes

The doctrine supports three reading modes. Choose the one that matches your situation.

### Mode 1 — First-Time Full Read (required once)
**When:** You have never operated under this doctrine before, or you need to understand the entire framework.
**What:** Read all 35 files in the Recommended Reading Order below.
**Exit condition:** After reading file 34, you are doctrine-activated. Proceed to the Operational Quickstart below to begin actual work.

### Mode 2 — Ongoing Session (default for returning AI)
**When:** You have already read the doctrine (or are operating under compact activation) and are starting a new work session.
**What:** Read only these files:
1. `14_RUNTIME_MASTER_PROMPT.md` — compact activation
2. `11_TASK_CLASSIFICATION_GUIDE.md` — classify the work
3. `21_OPERATIONAL_STATES.md` — determine the operational state
**Exit condition:** After classifying the work type and state, proceed to the Operational Quickstart below at the step that matches your classification.

### Mode 3 — Just-in-Time Reference (during work)
**When:** You are mid-work and need a specific protocol.
**What:** Read only the file that applies. The Operational Quickstart below maps work stages to files.
**Exit condition:** Apply the protocol and continue work. No full read required.

---

## Recommended Reading Order (Mode 1 only)

For first-time understanding, read in this order:

1. `00_START_HERE.md`
2. `01_DOCTRINE_FOUNDATION.md`
3. `02_OPERATIONAL_PRINCIPLES.md`
4. `03_PROJECT_LIFECYCLE.md`
5. `04_DISCOVERY_PROTOCOL.md`
6. `05_CONSOLIDATION_PROTOCOL.md`
7. `06_BUILD_READINESS_CHECKLIST.md`
8. `07_DELIVERY_PROTOCOL.md`
9. `08_DECISION_RULES.md`
10. `09_OUTPUT_QUALITY_STANDARD.md`
11. `10_GLOSSARY.md`
12. `11_TASK_CLASSIFICATION_GUIDE.md` — Task Classification Guide
13. `12_TEMPLATE_WORK_AGREEMENT.md` — Work Agreement Template
14. `13_PROJECT_SESSION_TEMPLATE.md`
15. `14_RUNTIME_MASTER_PROMPT.md`
16. `15_BROWNFIELD_DISCOVERY_PROTOCOL.md` — Brownfield Discovery Protocol
17. `16_ANTI_PATTERNS.md`
18. `17_VERSIONING_POLICY.md`
19. `18_EVOLUTION_LOG.md`
20. `19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md`
21. `20_ENFORCEMENT_LAYER.md` — Enforcement Layer
22. `21_OPERATIONAL_STATES.md` — Operational States (Exploratory, Formative, Stable)
23. `22_DISCOVERY_DIMENSION_PROTOCOL.md` — Discovery Dimension Protocol (13 dimension categories)
24. `23_TESTING_STRATEGY_PROTOCOL.md` — Testing Strategy (8 test types, test pyramid, coverage standards)
25. `24_ARCHITECTURE_DECISION_RECORDS.md` — ADR Protocol (decision records with context and rationale)
26. `25_OBSERVABILITY_PROTOCOL.md` — Observability (logs, metrics, traces, alerts, dashboards)
27. `26_SECURITY_REVIEW_PROTOCOL.md` — Security Review (3 levels: automated, manual, threat model)
28. `27_TECHNICAL_DEBT_PROTOCOL.md` — Technical Debt (7 types, Debt Register, payoff protocol)
29. `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md` — Dependency Management (evaluation, versioning, security)
30. `29_DOCUMENTATION_PROTOCOL.md` — Documentation (living docs, README requirements, quality standards)
31. `30_INCIDENT_RESPONSE_PROTOCOL.md` — Incident Response (SEV1-4, blameless post-mortems)
32. `31_QUALITY_GATES.md` — Quality Gates (gates at every stage transition)
33. `32_API_GOVERNANCE_PROTOCOL.md` — API Governance (naming, versioning, error handling, pagination)
34. `33_DATA_GOVERNANCE_PROTOCOL.md` — Data Governance (4 classification levels, handling, retention)
35. `34_METRICS_FEEDBACK_LOOP.md` — Metrics & Feedback Loop (DORA metrics, doctrine metrics, continuous improvement)

**Exit condition:** You have completed the full doctrine read. You are now doctrine-activated. To begin actual work, proceed to the Operational Quickstart below.

---

## Operational Quickstart

For actual live use, the doctrine operates in the following sequence for ALL work types.

### Step 1 — Classify the work
Use:
- `11_TASK_CLASSIFICATION_GUIDE.md` — Task Classification Guide
- `21_OPERATIONAL_STATES.md` — Operational States

Classify the work as Project, Feature, Refactoring, Bugfix, Task, or Question. This determines the lifecycle path and process depth.

**Also determine the Operational State** (Exploratory, Formative, or Stable) — this determines how strict the rules are, based on output preciousness. Default to Stable when unclear.

### Step 2 — Open the session correctly
Use:
- `13_PROJECT_SESSION_TEMPLATE.md`
- `14_RUNTIME_MASTER_PROMPT.md`

Activate the doctrine in the AI and establish the session context.

### Step 3 — Run discovery
Use:
- `04_DISCOVERY_PROTOCOL.md` — for greenfield work (new projects)
- `15_BROWNFIELD_DISCOVERY_PROTOCOL.md` — for brownfield work (existing systems)
- `22_DISCOVERY_DIMENSION_PROTOCOL.md` — for systematic dimension coverage (safety, compliance, NFRs, hardware, ML, migration, legacy, multi-team)
- `11_TASK_CLASSIFICATION_GUIDE.md` — for classification-driven intake

Discovery depth scales with work type: full discovery for projects and features, focused discovery for bugfixes, quick scan for tasks, none for questions. The Discovery Dimension Protocol ensures no dimension is missed regardless of domain.

### Step 4 — Consolidate the work
Use:
- `05_CONSOLIDATION_PROTOCOL.md`
- `12_TEMPLATE_WORK_AGREEMENT.md` — Work Agreement Template

Consolidate discovery findings into a coherent work agreement. For the Direct Path (questions), consolidation may be minimal or skipped.

### Step 5 — Verify readiness
Use:
- `06_BUILD_READINESS_CHECKLIST.md`

Readiness verification depth scales with work type. Full readiness gate for projects and features; lighter check for tasks; not applicable for questions.

### Step 6 — Begin structured delivery
Use:
- `07_DELIVERY_PROTOCOL.md`
- `08_DECISION_RULES.md`
- `09_OUTPUT_QUALITY_STANDARD.md`

For Stable state work, delivery also requires the mega-tech protocols:
- `23_TESTING_STRATEGY_PROTOCOL.md` — define what "100% verified" means for this work
- `24_ARCHITECTURE_DECISION_RECORDS.md` — record significant decisions
- `25_OBSERVABILITY_PROTOCOL.md` — add logs, metrics, traces, alerts
- `26_SECURITY_REVIEW_PROTOCOL.md` — security review at appropriate level
- `27_TECHNICAL_DEBT_PROTOCOL.md` — track any intentional debt
- `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md` — evaluate any new dependencies
- `29_DOCUMENTATION_PROTOCOL.md` — update living documentation
- `30_INCIDENT_RESPONSE_PROTOCOL.md` — if work touches production systems (incident readiness)
- `31_QUALITY_GATES.md` — pass all applicable quality gates
- `32_API_GOVERNANCE_PROTOCOL.md` — if touching APIs
- `33_DATA_GOVERNANCE_PROTOCOL.md` — if touching data
- `34_METRICS_FEEDBACK_LOOP.md` — define success metrics and feedback collection

For Formative state, these are lighter (see each protocol's state requirements).
For Exploratory state, these are not required (throwaway).

### Step 7 — Evolve the doctrine if needed
Use:
- `16_ANTI_PATTERNS.md`
- `17_VERSIONING_POLICY.md`
- `18_EVOLUTION_LOG.md`
- `19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md`

---

## How the Doctrine Must Behave in Practice

When applied correctly, this doctrine changes the interaction model between user and AI.

Instead of this:

- user vaguely describes something
- AI guesses
- work starts shallow
- hidden needs appear later
- architecture is patched reactively

The process becomes this:

- user presents an idea, need, pain, bug, or ambition
- AI classifies the work type
- AI expands awareness responsibly
- AI guides discovery without requiring expertise (greenfield or brownfield as appropriate)
- responses are consolidated into a formal work agreement
- readiness is checked before build
- structured delivery begins with seriousness and clarity

This is the intended behavior.

---

## Minimum Required Integrity of the Doctrine

The doctrine must remain operationally valid even without:
- precedent examples
- domain-specific prior cases
- external inspiration material

Its core strength must come from:
- principles
- protocols
- templates
- readiness checks
- quality standards
- explicit decision rules
- task classification

If the doctrine requires reference cases in order to function well, then the doctrine is not mature enough.

This framework must remain self-sufficient.

---

## Success Condition

A correct application of this doctrine produces the following result:

Work that begins with:
- correct classification
- structural clarity
- explicit scope logic
- controlled ambiguity
- transparent assumptions
- serious readiness
- proportionate ambition
- strong delivery direction

In short:

The doctrine succeeds when any engineering work — from a simple question to a full project — can be processed with the right depth of process, without depending on the user's technical expertise and without falling into shallow construction.

---

## Next Step

After reading this file, choose your path based on your situation (see **Reading Modes** above):

- **First-time reader** → continue to `01_DOCTRINE_FOUNDATION.md` (Mode 1: full read)
- **Returning AI starting a session** → read `14_RUNTIME_MASTER_PROMPT.md` + `11_TASK_CLASSIFICATION_GUIDE.md` + `21_OPERATIONAL_STATES.md` (Mode 2: ongoing session)
- **Mid-work needing a specific protocol** → read the relevant file from the Operational Quickstart below (Mode 3: just-in-time)
