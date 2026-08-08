# Engineering Work Doctrine

**Version 0.8.1** — Mega-tech ready, five-layer architecture, 35 files, 12 production-grade protocols.

A structured, AI-governed engineering framework that ensures work is never executed shallow, never architecturally blind, and never built before understanding is formally established.

---

## What This Is

The Engineering Work Doctrine is an operational system for AI-guided engineering work. It transforms raw ideas, vague intentions, bug reports, refactoring needs, and strategic ambitions into structured, validated, and build-ready work through a governed process.

It is not a prompt library. It is not a brainstorm archive. It is not a loose collection of notes. It is a **deterministic framework** that governs how AI tools classify, discover, consolidate, agree, verify, and deliver engineering work — from a simple question to a full project birth.

### Core Premise

The user is not required to be a software architect, systems analyst, product strategist, infrastructure engineer, database designer, security specialist, or UX designer in order to correctly define engineering work. **The AI must carry the burden of structural vision.**

### What It Governs

The doctrine governs ALL engineering work, not just new projects:

| Work Type | Lifecycle Path | Process Depth |
|-----------|----------------|---------------|
| Project | Full Lifecycle | Maximum — discovery, consolidation, agreement, readiness, delivery, evolution |
| Feature | Feature Path | Full — context discovery, change consolidation, agreement, delivery |
| Refactoring | Change Path | Focused — codebase analysis, change consolidation, delivery |
| Bugfix | Fix Path | Focused — problem discovery, fix consolidation, delivery |
| Task | Light Path | Light — task discovery, consolidation, delivery |
| Question | Direct Path | Minimal — direct answer, no agreement needed |

---

## AI Activation

**If you are an AI tool (Codex, Claude, Cursor, Windsurf, Gemini, or any LLM with file access):**

Read `AGENTS.md` at the workspace root before responding to any user request.

`AGENTS.md` is the sole AI activation document. It contains the full behavioral rules, ecosystem structure, operational state, root model, and doctrine map. Any AI that reads it and applies the rules is operating correctly under the doctrine, regardless of tool identity.

The doctrine is **AI-tool-agnostic**. Codex is the current preferred execution path — a strategic choice, not a structural dependency. See `OPERATIONS/TOOL_AGNOSTIC_PATH.md` for full compatibility details.

---

## The Five-Layer Architecture

The doctrine operates within a five-layer architecture. Each layer answers a different question:

```
┌─────────────────────────────────────────────────────────────┐
│  LAYER 1 — GOVERNANCE COGNITIVE (files 00-19)              │
│  "What work is this? How should it be approached?"          │
│  Classification, lifecycle, discovery, consolidation,       │
│  readiness, delivery, decision rules, quality, glossary,    │
│  templates, runtime prompt, anti-patterns, versioning       │
├─────────────────────────────────────────────────────────────┤
│  LAYER 2 — EXECUTION FLOW (file 07)                        │
│  "How to execute this work with mastery?"                   │
│  5-stage flow: ENTENDER → ESTUDAR → PLANEJAR →             │
│  EXECUTAR → VERIFICAR                                       │
├─────────────────────────────────────────────────────────────┤
│  LAYER 3 — ENFORCEMENT (files 20-22)                       │
│  "Is the work 100% correct? Prove it."                      │
│  Validators, gates, integrity protection, operational       │
│  states, discovery dimensions                               │
├─────────────────────────────────────────────────────────────┤
│  LAYER 4 — MEGA-TECH PROTOCOLS (files 23-34)               │
│  "Is this production-grade?"                                │
│  12 protocols scaling with operational state                │
├─────────────────────────────────────────────────────────────┤
│  LAYER 5 — CONSTITUTION (component of file 12)             │
│  "What are the non-negotiable rules of this project?"       │
│  Project-specific invariants, standards, prohibitions       │
└─────────────────────────────────────────────────────────────┘
```

No layer replaces another. Each operates at its own level. Together they cover the complete cycle from request to verified, production-grade delivery.

---

## Operational States

Every piece of work exists in one of three operational states. The state determines what rules apply — this is the key mechanism that allows the doctrine to scale from throwaway prototypes to production systems without over-engineering or under-engineering.

| State | When | Rules | Mega-tech |
|-------|------|-------|-----------|
| **Exploratory** | Spikes, prototypes, throwaway | Minimal process, no Rigid Payload, workarounds allowed | Skipped |
| **Formative** | Active development, iterating | Consolidation encouraged, lighter standards, payload on commit | Lighter |
| **Stable** | Production, live, precious | Full doctrine — all rules, all protocols, 100% non-negotiable | Full (all 12) |

Default to Stable when unclear. State is per-item, not per-project. The most critical transition is the **Consolidation Moment** (Formative → Stable), which has a mandatory ritual. See `ENGINEERING_WORK_DOCTRINE/21_OPERATIONAL_STATES.md`.

---

## The 12 Mega-Tech Protocols

These protocols define what "production-grade" means. They are mandatory in Stable state, lighter in Formative, and skipped in Exploratory.

| # | Protocol | File | What It Governs |
|---|----------|------|-----------------|
| 23 | Testing Strategy | `ENGINEERING_WORK_DOCTRINE/23_TESTING_STRATEGY_PROTOCOL.md` | 8 test types, test pyramid, coverage standards |
| 24 | Architecture Decision Records | `ENGINEERING_WORK_DOCTRINE/24_ARCHITECTURE_DECISION_RECORDS.md` | Decision records with context and rationale |
| 25 | Observability | `ENGINEERING_WORK_DOCTRINE/25_OBSERVABILITY_PROTOCOL.md` | Logs, metrics, traces, alerts, dashboards |
| 26 | Security Review | `ENGINEERING_WORK_DOCTRINE/26_SECURITY_REVIEW_PROTOCOL.md` | 3 levels: automated, manual, threat model |
| 27 | Technical Debt | `ENGINEERING_WORK_DOCTRINE/27_TECHNICAL_DEBT_PROTOCOL.md` | 7 debt types, Debt Register, payoff protocol |
| 28 | Dependency Management | `ENGINEERING_WORK_DOCTRINE/28_DEPENDENCY_MANAGEMENT_PROTOCOL.md` | Evaluation, versioning, security scanning |
| 29 | Documentation | `ENGINEERING_WORK_DOCTRINE/29_DOCUMENTATION_PROTOCOL.md` | Living docs, README requirements, quality standards |
| 30 | Incident Response | `ENGINEERING_WORK_DOCTRINE/30_INCIDENT_RESPONSE_PROTOCOL.md` | SEV1-4, blameless post-mortems |
| 31 | Quality Gates | `ENGINEERING_WORK_DOCTRINE/31_QUALITY_GATES.md` | Gates at every stage transition |
| 32 | API Governance | `ENGINEERING_WORK_DOCTRINE/32_API_GOVERNANCE_PROTOCOL.md` | Naming, versioning, error handling, pagination |
| 33 | Data Governance | `ENGINEERING_WORK_DOCTRINE/33_DATA_GOVERNANCE_PROTOCOL.md` | 4 classification levels, handling, retention |
| 34 | Metrics & Feedback Loop | `ENGINEERING_WORK_DOCTRINE/34_METRICS_FEEDBACK_LOOP.md` | DORA metrics, doctrine metrics, continuous improvement |

Each protocol includes: Purpose, Operational State requirements, Rigid Payload format, Anti-Patterns, Consolidation Moment reference, and Success Condition.

---

## The Execution Flow

Within delivery, the doctrine mandates a 5-stage execution flow:

```
ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR
```

1. **ENTENDER** — understand what is being asked and what success looks like
2. **ESTUDAR** — study the codebase, patterns, constraints, and root cause
3. **PLANEJAR** — plan the direct path: files, functions, changes needed
4. **EXECUTAR** — execute with the first execution being the correct one
5. **VERIFICAR** — verify 100%: validators pass, tests pass, no regressions

This flow is embedded in `AGENTS.md` and `ENGINEERING_WORK_DOCTRINE/14_RUNTIME_MASTER_PROMPT.md` for compact activation.

---

## Non-Negotiable Rules

These rules apply across all work types. They are refined by operational state but never eliminated:

- **Classify before acting** — work type AND operational state
- **Discovery before architecture** — understand before designing
- **Consolidation before agreement** — organize before committing
- **Agreement before build** — confirm before constructing
- **Readiness before delivery** — verify before shipping
- **No work files created outside doctrinal action**
- **No assumption treated as confirmed fact**
- **Proportionality** — process depth must match work complexity
- **100% as Floor** — below 100%, work is not done (refined by operational state)
- **No workarounds** — prohibited in Stable state, allowed in Exploratory/Formative with notes
- **Rigid Payload** — implementation output must include Diagnóstico, Alterações, Enforcement, Rollback
- **Consolidation Moment** — mandatory before work enters Stable state
- **Mega-tech protocols** — mandatory in Stable state, proportional in Formative, skipped in Exploratory

---

## How to Set Up

### Option A — Standalone Governance Workspace

Use DocsSB as a standalone governance root that manages multiple projects:

```
[workspace-root]/
├── DocsSB/                          ← this repository (governance root)
│   ├── README.md
│   ├── AGENTS.md
│   ├── ENGINEERING_WORK_DOCTRINE/
│   ├── DECISIONS/
│   ├── ENVIRONMENT/
│   └── OPERATIONS/
├── Projects/                        ← active and archived project instances
└── AgentRuntime/                    ← runtime artifacts
```

1. Clone this repository into your workspace root as `DocsSB/`
2. Ensure `AGENTS.md` is present at the governance root
3. Ensure `ENGINEERING_WORK_DOCTRINE/` has all 35 files (00-34)
4. Run the preflight checklist: `OPERATIONS/PREFLIGHT_CHECKLIST.md`

### Option B — Deploy Into an Existing Project

Use the doctrine inside a project that already has its own structure:

```
my-project/
├── README.md                        ← your project's README (keep it, do NOT overwrite)
├── AGENTS.md                        ← extract from DocsSB (AI activation)
├── ENGINEERING_WORK_DOCTRINE/       ← extract from DocsSB (35 files)
├── DECISIONS/                       ← extract from DocsSB
├── ENVIRONMENT/                     ← extract from DocsSB
├── OPERATIONS/                      ← extract from DocsSB
├── src/
└── package.json
```

**Critical:** Extract everything **except** `README.md`. Your project already has its own README — the doctrine's README is for standalone governance use only. The `AGENTS.md` file is the AI entry point and does not conflict with your project's README.

**No conflicts:** `AGENTS.md` is the AI activation file (read by AI tools). `README.md` is your project's documentation (read by humans). They coexist without collision.

### Path Agnosticism

No document in this workspace hardcodes a physical root path. All references are expressed as structural roles and relative relationships. The workspace may live on any medium — pendrive, SSD, local disk, remote volume. The physical location is not structurally relevant.

### Root Model

| Role | Conventional name | Relationship |
|------|-------------------|--------------|
| Workspace root | (user-defined) | Top-level directory. Contains governance root, projects root, runtime root |
| Governance root | `DocsSB/` | Contains doctrine, decisions, environment state, operations docs |
| Doctrine root | `ENGINEERING_WORK_DOCTRINE/` | Inside governance root. 35 files (00-34) |
| Projects root | `Projects/` | Inside workspace root. Active and archived project instances |
| Runtime root | `AgentRuntime/` | Inside workspace root. Runtime artifacts |

---

## How to Run

The doctrine is not a runtime application — it is a governance framework. To "run" it:

1. Open the workspace root in your AI tool (Codex, Claude, Cursor, Windsurf, Gemini)
2. The AI reads `AGENTS.md` and activates doctrinal behavior automatically
3. Issue any engineering work request — the AI will:
   - Classify the work type (Project, Feature, Refactoring, Bugfix, Task, Question)
   - Determine the operational state (Exploratory, Formative, Stable)
   - Conduct discovery (greenfield or brownfield as appropriate)
   - Consolidate findings into a work agreement
   - Verify build readiness
   - Execute the 5-stage delivery flow (ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR)
   - Apply mega-tech protocols proportional to operational state
   - Run the Consolidation Moment before transitioning to Stable

For the full activation sequence, see `OPERATIONS/MAIN_PATH_RITUAL.md`.

For tool-specific paths, see `OPERATIONS/CODEX_MAIN_PATH.md` and `OPERATIONS/TOOL_AGNOSTIC_PATH.md`.

---

## How to Test

The doctrine's integrity is verified through multiple layers:

**Preflight verification:**
- `OPERATIONS/PREFLIGHT_CHECKLIST.md` — verifies workspace structure and readiness before any work session

**Readiness verification:**
- `ENVIRONMENT/MAIN_PATH_READINESS.md` — verifies doctrine version alignment and activation capability

**Consistency audit (27 categories):**
- File references (no broken cross-references)
- Version numbers (all files at 0.8.1)
- Section naming (standardized across all 12 mega-tech protocols)
- Cross-references (mega-tech protocols reference each other correctly)
- Anti-pattern coverage (42 anti-patterns, all 12 protocols have domain-specific anti-patterns)
- Mega-tech protocol completeness (all 12 protocols have Operational State, Rigid Payload, Consolidation Moment, Anti-Patterns, and Success Condition sections)
- README/AGENTS separation (AI activation decoupled from project README)

**Enforcement layer:**
- `ENGINEERING_WORK_DOCTRINE/20_ENFORCEMENT_LAYER.md` — validators, gates, integrity protection
- `ENGINEERING_WORK_DOCTRINE/31_QUALITY_GATES.md` — 14 quality gates at every stage transition

---

## How to Deploy

### Deploying to a new project

1. Create the project directory structure under `Projects/` in your workspace root
2. Follow the Full Lifecycle path (Raw Impulse → Guided Discovery → Consolidation → Work Agreement → Readiness → Delivery → Evolution)
3. The doctrine will guide project birth through `ENGINEERING_WORK_DOCTRINE/04_DISCOVERY_PROTOCOL.md` and `ENGINEERING_WORK_DOCTRINE/12_TEMPLATE_WORK_AGREEMENT.md`

### Deploying alongside an existing project

1. Copy `AGENTS.md`, `ENGINEERING_WORK_DOCTRINE/`, `DECISIONS/`, `ENVIRONMENT/`, and `OPERATIONS/` into the project root
2. **Do NOT copy `README.md`** — the project already has its own
3. The AI will read `AGENTS.md` and operate doctrinally over the existing codebase
4. For existing codebase work, the doctrine uses `ENGINEERING_WORK_DOCTRINE/15_BROWNFIELD_DISCOVERY_PROTOCOL.md` (understand what exists before changing it)

### Deploying as a standalone governance workspace

1. Clone this repository as `DocsSB/` inside your workspace root
2. Create `Projects/` and `AgentRuntime/` directories at the workspace root
3. Run `OPERATIONS/PREFLIGHT_CHECKLIST.md` to verify readiness
4. Begin work through `OPERATIONS/MAIN_PATH_RITUAL.md`

---

## Where to Find Architecture Docs

### Doctrine entry point
`ENGINEERING_WORK_DOCTRINE/00_START_HERE.md` — full doctrine overview, reading modes, operational quickstart, directory map

### Five-layer architecture
`ENGINEERING_WORK_DOCTRINE/20_ENFORCEMENT_LAYER.md` — complete architecture description with layer interactions

### Compact activation
`ENGINEERING_WORK_DOCTRINE/14_RUNTIME_MASTER_PROMPT.md` — compact prompt for ongoing sessions (Mode 2)

### Session template
`ENGINEERING_WORK_DOCTRINE/13_PROJECT_SESSION_TEMPLATE.md` — work session opening template

### Task classification
`ENGINEERING_WORK_DOCTRINE/11_TASK_CLASSIFICATION_GUIDE.md` — full classification protocol

### Operational states
`ENGINEERING_WORK_DOCTRINE/21_OPERATIONAL_STATES.md` — Exploratory, Formative, Stable, Consolidation Moment ritual

### Enforcement
`ENGINEERING_WORK_DOCTRINE/20_ENFORCEMENT_LAYER.md` — validators, gates, integrity protection

### Anti-patterns
`ENGINEERING_WORK_DOCTRINE/16_ANTI_PATTERNS.md` — 42 anti-patterns across all categories

### Glossary
`ENGINEERING_WORK_DOCTRINE/10_GLOSSARY.md` — doctrine-layer terminology

---

## Where to Find Runbooks

| Runbook | Location | Purpose |
|---------|----------|---------|
| Preflight Checklist | `OPERATIONS/PREFLIGHT_CHECKLIST.md` | Verify workspace before starting a session |
| Main Path Ritual | `OPERATIONS/MAIN_PATH_RITUAL.md` | Full operating ritual for the main path |
| Codex Path | `OPERATIONS/CODEX_MAIN_PATH.md` | Codex-specific operating path |
| Tool-Agnostic Path | `OPERATIONS/TOOL_AGNOSTIC_PATH.md` | Tool compatibility and agnosticism details |
| Environment Status | `ENVIRONMENT/CURRENT_ENVIRONMENT_STATUS.md` | Current workspace environment state |
| Readiness Checklist | `ENVIRONMENT/MAIN_PATH_READINESS.md` | Main path readiness verification |
| Decisions | `DECISIONS/` | Formal strategic decisions (current phase, AI path, validation) |

---

## How to Contribute

1. **Read the doctrine:** Start with `ENGINEERING_WORK_DOCTRINE/00_START_HERE.md` (Mode 1: full read)
2. **Follow the classification guide:** `ENGINEERING_WORK_DOCTRINE/11_TASK_CLASSIFICATION_GUIDE.md`
3. **Respect the versioning policy:** `ENGINEERING_WORK_DOCTRINE/17_VERSIONING_POLICY.md` — all changes must follow semantic versioning
4. **Log all structural changes:** `ENGINEERING_WORK_DOCTRINE/18_EVOLUTION_LOG.md` — no silent growth
5. **Apply the structural recomposition principle:** `ENGINEERING_WORK_DOCTRINE/19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md` — when restructuring, preserve semantic integrity
6. **No project instance should be manually created outside doctrinal action**

### Vocabulary Layers

The ecosystem uses two intentional vocabulary layers:

- **Governance layer** (`AGENTS.md`, `README.md`, `DECISIONS/`, `ENVIRONMENT/`, `OPERATIONS/`) — uses workspace vocabulary: workspace root, governance root, doctrine root, projects root, runtime root, main path, readiness
- **Doctrine layer** (`ENGINEERING_WORK_DOCTRINE/`) — uses framework vocabulary: ecosystem, reusable artifact layer, PREI, structural recomposition, work agreement, lacuna, maximum plausible horizon, task classification, proportionality

These layers are intentionally distinct. The governance layer speaks about *where* the ecosystem operates; the doctrine layer speaks about *how* work is governed.

---

## Repository Structure

```
DocsSB/
├── README.md                                    ← You are here. Workspace README (for humans).
├── AGENTS.md                                    ← AI activation (sole entry point for any AI).
├── DECISIONS/                                   ← Formal strategic decisions.
│   ├── 0001_CURRENT_PHASE.md
│   ├── 0002_MAIN_AI_PATH.md
│   └── 0003_MAIN_PATH_VALIDATED.md
├── ENVIRONMENT/                                 ← Workspace structure and readiness state.
│   ├── CURRENT_ENVIRONMENT_STATUS.md
│   └── MAIN_PATH_READINESS.md
├── OPERATIONS/                                  ← Operating rituals and path definitions.
│   ├── TOOL_AGNOSTIC_PATH.md
│   ├── CODEX_MAIN_PATH.md
│   ├── MAIN_PATH_RITUAL.md
│   └── PREFLIGHT_CHECKLIST.md
└── ENGINEERING_WORK_DOCTRINE/                   ← Full doctrine (35 files: 00-34).
    ├── 00_START_HERE.md                         ← Doctrine entry point.
    ├── 01_DOCTRINE_FOUNDATION.md
    ├── 02_OPERATIONAL_PRINCIPLES.md
    ├── 03_PROJECT_LIFECYCLE.md
    ├── 04_DISCOVERY_PROTOCOL.md
    ├── 05_CONSOLIDATION_PROTOCOL.md
    ├── 06_BUILD_READINESS_CHECKLIST.md
    ├── 07_DELIVERY_PROTOCOL.md
    ├── 08_DECISION_RULES.md
    ├── 09_OUTPUT_QUALITY_STANDARD.md
    ├── 10_GLOSSARY.md
    ├── 11_TASK_CLASSIFICATION_GUIDE.md
    ├── 12_TEMPLATE_WORK_AGREEMENT.md
    ├── 13_PROJECT_SESSION_TEMPLATE.md
    ├── 14_RUNTIME_MASTER_PROMPT.md
    ├── 15_BROWNFIELD_DISCOVERY_PROTOCOL.md
    ├── 16_ANTI_PATTERNS.md
    ├── 17_VERSIONING_POLICY.md
    ├── 18_EVOLUTION_LOG.md
    ├── 19_STRUCTURAL_RECOMPOSITION_PRINCIPLE.md
    ├── 20_ENFORCEMENT_LAYER.md
    ├── 21_OPERATIONAL_STATES.md
    ├── 22_DISCOVERY_DIMENSION_PROTOCOL.md
    ├── 23_TESTING_STRATEGY_PROTOCOL.md
    ├── 24_ARCHITECTURE_DECISION_RECORDS.md
    ├── 25_OBSERVABILITY_PROTOCOL.md
    ├── 26_SECURITY_REVIEW_PROTOCOL.md
    ├── 27_TECHNICAL_DEBT_PROTOCOL.md
    ├── 28_DEPENDENCY_MANAGEMENT_PROTOCOL.md
    ├── 29_DOCUMENTATION_PROTOCOL.md
    ├── 30_INCIDENT_RESPONSE_PROTOCOL.md
    ├── 31_QUALITY_GATES.md
    ├── 32_API_GOVERNANCE_PROTOCOL.md
    ├── 33_DATA_GOVERNANCE_PROTOCOL.md
    └── 34_METRICS_FEEDBACK_LOOP.md
```

---

## Current Operational State

- **Doctrine version:** `0.8.1` — mega-tech ready, 35 files (00-34), full delivery stack
- **Architecture:** Five-layer (Governance Cognitive, Execution Flow, Enforcement, Mega-tech Protocols, Constitution)
- **Mega-tech protocols:** 12 protocols (files 23-34), all operational for Stable state
- **Anti-patterns:** 42 anti-patterns across all categories
- **Quality gates:** 14 gates at every stage transition
- **Doctrine-guided workspace reading:** validated through main path
- **First official pilot project:** not yet created — this is the pending next step
- **Main AI path:** Codex (current preference) — doctrine is tool-agnostic
- **Consistency audit:** 27/27 categories with zero issues

---

## Version History

| Version | Date | What Changed |
|---------|------|--------------|
| 0.6.0 | — | Enforcement Layer (file 20), original architecture (later expanded to five-layer in v0.8.1) |
| 0.6.1 | — | Stress-test hardening (user override, state persistence, refactoring without tests, false positive) |
| 0.7.0 | — | Operational State dimension (file 21), state-aware rules |
| 0.7.1 | — | Discovery Dimension Protocol (file 22), 13 dimension categories |
| 0.8.0 | — | Mega-tech delivery stack (files 23-34: 12 production-grade protocols) |
| 0.8.1 | — | Ecosystem audit corrections, five-layer architecture, Rigid Payload standardization, Consolidation Moment unified, README/AGENTS separation, conditional reading flow |

See `ENGINEERING_WORK_DOCTRINE/18_EVOLUTION_LOG.md` for the complete evolution history.

---

## License

This is a personal engineering governance framework. See `ENGINEERING_WORK_DOCTRINE/17_VERSIONING_POLICY.md` for versioning and governance rules.
