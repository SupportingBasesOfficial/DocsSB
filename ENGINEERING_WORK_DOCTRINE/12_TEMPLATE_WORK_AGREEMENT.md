# TEMPLATE — WORK AGREEMENT

## Purpose of This File

This file defines the official Work Agreement templates of the Engineering Work Doctrine.

A Work Agreement is the formal artifact that marks the transition from:
- discovered work
- to agreed work

It exists to prevent work from entering serious delivery as:
- a loose idea
- a fragmented clarification set
- an emotionally compelling but structurally unstable intention
- a partially understood request masquerading as defined work

The Work Agreement is the doctrine's formal threshold artifact.

Work becomes legitimately ready for execution only when its meaning can be expressed through a coherent agreement at the appropriate depth.

---

## Tiered Agreement System

The doctrine provides multiple agreement tiers, each scaled to the work type:

| Tier | Work Type | Depth | Sections |
|------|-----------|-------|----------|
| Full Work Agreement | Project | Maximum | All 21 sections below |
| Feature Specification | Feature | High | Sections 1-6, 15-16, 20 (adapted) |
| Change Plan | Refactoring | High | Sections 1-3, 15-16, 20 (adapted for change) |
| Fix Plan | Bugfix | Medium | Sections 1-3, 15-16, 20 (adapted for fix) |
| Task Brief | Task | Low | Sections 1-3, 20 (minimal) |
| Direct | Question | None | No formal agreement needed |

The AI must select the appropriate tier based on the task classification (see `11_TASK_CLASSIFICATION_GUIDE.md`).

---

## Usage Rule

Any agreement tier must be used only after:
1. discovery has been sufficiently conducted (at the appropriate depth)
2. consolidation has been completed (at the appropriate depth)
3. the work can be expressed coherently
4. open items have been surfaced and classified

An agreement must **not** be used as a substitute for discovery.

It must also **not** be treated as a casual summary.

A Work Agreement is a structural definition artifact.

---

## Agreement Rule

A valid Work Agreement must, at the appropriate depth for its tier:

- state what the work is
- state what the work is not (where applicable)
- state what it exists to accomplish
- state who it serves (where applicable)
- state what has been confirmed
- state what remains open
- state the main structural implications (where applicable)
- state the current readiness posture (where applicable)
- state what may legitimately happen next

Without the elements appropriate to its tier, the agreement is incomplete.

---

## AI Usage Guidance

When producing any agreement, the AI must:

- remain explicit
- remain truthful about uncertainty
- distinguish confirmed from inferred from recommended from open
- preserve the difference between scope and horizon (where applicable)
- avoid premature deep architecture unless the agreement is explicitly coupled to readiness-validated delivery
- make the work legible as an engineering object
- keep the agreement specific to the work
- avoid generic placeholder thinking

An agreement is not a marketing summary.
It is a structural artifact.

---

# FULL WORK AGREEMENT (Projects)

The following full template is used for the Full Lifecycle path (new projects).

For lighter tiers, see the adapted templates after this section.

## 1. Agreement Header

### Work Name
[ ]

### Agreement Version
[ ]

### Date
[ ]

### Prepared By
[AI / user / session identifier]

### Doctrine Context
This agreement was created under the Engineering Work Doctrine and represents the formal initiation state of the work at the current stage of maturity.

---

## 2. Work Identity

### 2.1 What the Work Is
A concise but structurally meaningful statement of what the work fundamentally is.

[ ]

### 2.2 What the Work Is Not
A concise statement of what the work is explicitly not trying to be at this stage.

[ ]

### 2.3 Operational Class
Examples:
- internal system
- SaaS platform
- workflow tool
- offline workspace
- operational dashboard
- business control system
- automation layer
- hybrid environment

[ ]

---

## 3. Work Purpose

### 3.1 Core Purpose
What this work exists to make possible.

[ ]

### 3.2 Problem / Need / Opportunity
What real need, pain, opportunity, or transformation this work responds to.

[ ]

### 3.3 Success Condition
What would make this work meaningfully successful in real use.

[ ]

### 3.4 Failure Condition
What would make this work unacceptable even if partially functional.

[ ]

---

## 4. Users, Actors, and Responsibility Model

### 4.1 Primary Actors
Who directly uses or depends on the project.

[ ]

### 4.2 Secondary Actors
Who matters indirectly, such as admins, managers, external systems, suppliers, approvers, customers, or service processes.

[ ]

### 4.3 Responsibility Differences
What meaningful distinctions exist between actors.
Examples:
- admin vs operator
- manager vs viewer
- creator vs approver
- internal user vs external user

[ ]

### 4.4 Actor-Control Implications
What the actor model already implies about access, visibility, permissions, or governance.

[ ]

---

## 5. Operational Reality and Core Flows

### 5.1 Operational Context
What real-world environment, workflow, or operational reality this project must support.

[ ]

### 5.2 Core Flows
What the main repeated or decisive flows are.

[ ]

### 5.3 State / Status Logic
What meaningful statuses, transitions, completions, approvals, closures, reversals, or flow states matter.

[ ]

### 5.4 Event Sensitivity
What actions or events the project must react to, enforce, or recognize as important.

[ ]

---

## 6. Data, Records, and Memory Requirements

### 6.1 Core Records
What core information this project must persist.

[ ]

### 6.2 Historical Needs
What actions, changes, approvals, events, or states should remain historically visible.

[ ]

### 6.3 Traceability Needs
What must be traceable or auditable.

[ ]

### 6.4 Metric / Reporting / Summary Implications
What totals, dashboards, metrics, indicators, summaries, or monitoring outputs are already implied.

[ ]

---

## 7. Control, Governance, and Safety Implications

### 7.1 Permission and Access Implications
What access distinctions or controls are required.

[ ]

### 7.2 Governance Needs
What approvals, responsibilities, auditability, action locks, or accountability mechanisms matter.

[ ]

### 7.3 Sensitive Operations
What operations require extra seriousness because they affect money, inventory, trust, compliance, visibility, identity, access, or irreversible change.

[ ]

### 7.4 Safety / Reliability Implications
What this project already implies about consistency, integrity, recovery, backup thinking, or operational reliability.

[ ]

---

## 8. Experience Expectations

### 8.1 Experience Character
What kind of system experience is expected.
Examples:
- simple and fast
- guided and low-friction
- operational and robust
- mobile-first
- desktop-first
- control-oriented
- highly accessible for non-technical users

[ ]

### 8.2 Device / Usage Context
What environments or devices the project must respect.

[ ]

### 8.3 Ergonomic Priorities
What usability priorities matter most.

[ ]

---

## 9. Automation, Alerts, and Intelligence

### 9.1 Automation Expectations
What should be automated now or structurally anticipated.

[ ]

### 9.2 Alert / Notification Implications
What kinds of events, failures, or thresholds should generate attention.

[ ]

### 9.3 Intelligence Support Expectations
Whether the project should eventually assist users through suggestions, classifications, summaries, or decision support.

[ ]

### 9.4 Automation Centrality
Whether automation is central, supportive, minimal, or still undefined.

[ ]

---

## 10. Environment and Technical Reality

### 10.1 Operating Environment
What environment this project is expected to live in.
Examples:
- cloud
- local
- browser
- mobile
- offline workspace
- hybrid environment

[ ]

### 10.2 Connectivity Reality
Whether the project assumes always-online, occasionally offline, or offline-capable operation.

[ ]

### 10.3 Environment Constraints
What real constraints the environment imposes.

[ ]

### 10.4 Environment Separation Implications
What separation needs already exist.
Examples:
- development vs production
- test vs live
- local vs cloud
- personal vs organizational

[ ]

---

## 11. Constraints and Context Reality

### 11.1 Real Constraints
What real limits shape the project.
Examples:
- time
- money
- device reality
- low support capacity
- small team
- mobile-first work
- low technical overhead tolerance

[ ]

### 11.2 Ownership / Maintainability Constraints
What constraints matter regarding long-term operation, maintenance, or system ownership.

[ ]

### 11.3 Practical Rejection Conditions
What kinds of technically beautiful but operationally impractical solutions would be unacceptable.

[ ]

---

## 12. Maximum Plausible Horizon

### 12.1 Plausible Future Horizon
What this project could realistically evolve into if it grows in importance, scale, sophistication, or reach.

[ ]

### 12.2 Why Horizon Awareness Matters Here
Why the plausible horizon matters structurally, even if not everything belongs to current scope.

[ ]

This section exists to preserve structural seriousness without inflating current commitments.

---

## 13. Structural Foundation Needed at Birth

### 13.1 Birth-Critical Structural Needs
What must already be respected from the beginning to avoid irresponsible project birth.

[ ]

### 13.2 Structural Protections Recommended at Birth
What protections or structural disciplines are recommended even if not explicitly requested.

[ ]

### 13.3 What Must Not Be Ignored at Birth
What would be expensive, dangerous, or distorting to ignore now.

[ ]

---

## 14. Confirmed Present Scope

### 14.1 What Is Clearly In Scope Now
What the project is definitely responsible for at its current confirmed birth state.

[ ]

### 14.2 What Is Explicitly Out of Scope Now
What the project is not committing to at the current stage.

[ ]

### 14.3 What Is Likely Future Scope, But Not Current Scope
What belongs to plausible evolution rather than immediate project obligation.

[ ]

This section is mandatory to prevent scope inflation and scope confusion.

---

## 15. Truth Status Map

### 15.1 Confirmed
What has been directly confirmed by the user or formal project clarification.

[ ]

### 15.2 Inferred
What is not directly stated but strongly implied by the discovery and consolidation outputs.

[ ]

### 15.3 Recommended
What the AI recommends as best practice or structural protection.

[ ]

### 15.4 Open
What remains unresolved, undefined, or pending clarification.

[ ]

This section is mandatory for doctrinal truthfulness.

---

## 16. Lacuna Classification

### 16.1 Critical Blocking Lacunae
What unresolved items prevent responsible progression, if any.

[ ]

### 16.2 Important Non-Blocking Lacunae
What unresolved items matter but do not invalidate legitimate progress.

[ ]

### 16.3 Evolutive Lacunae
What unresolved items belong naturally to later maturity and should not block birth.

[ ]

This section is mandatory for lacuna governance.

---

## 17. Structural Implication Summary

What high-level architectural, governance, data, operational, or environment consequences already follow from the known material.

Examples:
- likely need for role-based access
- likely need for auditable operations
- likely need for stateful workflows
- likely need for separation of environments
- likely need for mobile-first design
- likely need for offline-aware architecture
- likely need for transaction integrity
- likely need for multi-unit partitioning

[ ]

This section must stay at implication level unless deeper delivery has already been authorized.

---

## 18. Readiness Posture

### 18.1 Current Readiness Status
Choose one:
- Ready for Structured Delivery
- Not Ready
- Conditionally Ready
- Return Required to Earlier Stage

[ ]

### 18.2 Why This Status Was Reached
[ ]

### 18.3 What Is Already Mature Enough
[ ]

### 18.4 What Still Prevents or Conditions Progress
[ ]

### 18.5 Correct Next Step
Choose one:
- More Discovery
- More Consolidation
- Contract Refinement
- Build Readiness Approval
- Structured Delivery

[ ]

This section connects the contract to the lifecycle.

---

## 19. Authorized Delivery Direction

### 19.1 What Delivery Is Legitimate Now
What the AI may legitimately begin delivering at the current maturity level.

[ ]

### 19.2 What Delivery Is Not Yet Legitimate
What should not yet be delivered because readiness, clarity, or scope legitimacy is insufficient.

[ ]

### 19.3 Recommended Immediate Delivery Focus
What should be delivered first if structured delivery begins.

[ ]

This prevents delivery from overreaching.

---

## 20. Contract Summary

### Executive Birth Summary
A concise final statement describing:
- what this project now is
- what it must support
- what has been confirmed
- what remains open
- what structural seriousness it requires
- what should happen next

[ ]

---

## 21. Constitution (Project-Specific Invariants)

The Constitution defines the non-negotiable rules of this specific project. While the doctrine is universal, the Constitution is local — it defines what this particular project must always respect.

The Constitution is the bridge between the work agreement (what the work is) and the enforcement layer (how the work is verified). See `20_ENFORCEMENT_LAYER.md`.

### 21.1 Invariantes
Rules that must always hold for this project.

Examples:
- Every function has explicit return type
- Every exported function has tests
- No `any` in TypeScript
- No `console.log` in production (use structured logger)
- Every change passes the applicable validators
- Every function under 50 lines
- Imports organized: external → internal

[ ]

### 21.2 Direção
Project direction and priorities.

- Objective: [ ]
- Priority (e.g., functionality > performance > aesthetics): [ ]
- Operational State: [Exploratory | Formative | Stable] — determines which rules apply (see `21_OPERATIONAL_STATES.md`)
- Definition of done: 100% of the acceptance criterion for the work type (refined by Operational State)

[ ]

### 21.3 Padrões
Technical standards for this project.

- Language: [ ]
- Runtime: [ ]
- Linter: [ ]
- Test framework: [ ]

[ ]

### 21.4 Proibições
What is never allowed in this project.

Examples:
- Workarounds in Stable state (always resolve root cause; allowed in Exploratory/Formative with notes — see `21_OPERATIONAL_STATES.md`)
- `any` in TypeScript (use `unknown` + type guard)
- `console.log` in production (use structured logger)
- Unused imports
- Functions over 50 lines
- TODO/FIXME/HACK in code
- Empty try/catch that silences errors
- Forced casts (`as any`, `as unknown as X`)
- Duplicated logic
- Abstractions used only once

[ ]

### 21.5 Configuração de Validação
Validation configuration for enforcement.

- requireTests: [true/false]
- preCommitTimeout: [seconds]
- prePushTimeout: [seconds]
- ciTimeout: [seconds]
- mutationThreshold: [percentage]
- coverageThreshold: [percentage]

[ ]

### 21.6 Validators Applicable
Which validators apply to this project (per proportional enforcement):

[ ]

### 21.7 Mega-tech Protocol Requirements (Stable State)

When this work is in Stable state, the following mega-tech protocols apply. Each must be addressed in the work agreement:

- **Testing strategy** — which test types are required for this work type? (`23_TESTING_STRATEGY_PROTOCOL.md`)
- **ADRs** — will significant architectural decisions be made? If yes, ADRs are required. (`24_ARCHITECTURE_DECISION_RECORDS.md`)
- **Observability** — what logs, metrics, traces, alerts are needed? (`25_OBSERVABILITY_PROTOCOL.md`)
- **Security review level** — L1 (automated), L2 (manual), or L3 (external)? (`26_SECURITY_REVIEW_PROTOCOL.md`)
- **Technical debt** — is intentional debt expected? If yes, how will it be tracked? (`27_TECHNICAL_DEBT_PROTOCOL.md`)
- **Dependencies** — will new dependencies be added? If yes, evaluation is required. (`28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`)
- **Documentation** — what documentation types need updating? (`29_DOCUMENTATION_PROTOCOL.md`)
- **Incident response** — is this work deployed to production? If yes, incident response readiness is required. (`30_INCIDENT_RESPONSE_PROTOCOL.md`)
- **Quality gates** — which gates apply at each stage transition? (`31_QUALITY_GATES.md`)
- **API governance** — does this work touch API surfaces? If yes, governance check required. (`32_API_GOVERNANCE_PROTOCOL.md`)
- **Data governance** — does this work touch data? If yes, data classification required. (`33_DATA_GOVERNANCE_PROTOCOL.md`)
- **Metrics** — what success metrics will be tracked? (`34_METRICS_FEEDBACK_LOOP.md`)

In Formative state, these are lighter. In Exploratory state, these are not required.

[ ]

### 21.8 Rigid Payload Format (Implementation Output)

When implementation begins, the AI's output must follow the Rigid Payload format defined in `09_OUTPUT_QUALITY_STANDARD.md`. The Rigid Payload has 4 mandatory sections:

- **Diagnóstico** — what was the problem, what was found, what is the root cause
- **Alterações** — what was changed, file by file, with justification
- **Enforcement** — how the changes were verified (tests, validators, security checks, quality gates)
- **Rollback** — how to undo the changes if something goes wrong

The Rigid Payload is required in Stable state, required on-commit in Formative state, and not required in Exploratory state. See `09_OUTPUT_QUALITY_STANDARD.md` for the full format definition and `21_OPERATIONAL_STATES.md` for state-specific requirements.

[ ]

---

## Agreement Completion Rule

Any agreement is complete only when the elements appropriate to its tier are present:

- the work is clearly identifiable
- scope and horizon are explicitly separated (where applicable)
- truth status is preserved
- lacunae are classified (where applicable)
- structural implications are visible (where applicable)
- readiness posture is stated (where applicable)
- next-step legitimacy is clear

If the required elements for the tier are not present, the agreement is incomplete.

---

## Agreement Success Condition

A Work Agreement has been successfully created when:

- the work has become a formal engineering object
- the work is no longer just "clarified," but structurally defined
- work identity is explicit
- scope is bounded
- uncertainty is governed
- doctrinal truthfulness is preserved
- readiness can now be judged or acted on explicitly (where applicable)
- the work can legitimately move forward without false coherence

That is the official success condition of the Work Agreement.

---

# LIGHTER AGREEMENT TIERS

The following templates are used for non-project work types. They are lighter than the Full Work Agreement but still formal enough to prevent undefined work from entering execution.

---

# FEATURE SPECIFICATION (Features)

Used for the Feature Path — adding new capability to an existing system.

## F1. Feature Header
### Feature Name: [ ]
### Existing System: [ ]
### Date: [ ]

## F2. Feature Identity
### What the feature is: [ ]
### What the feature is not: [ ]
### How it integrates with the existing system: [ ]

## F3. Feature Purpose
### What need this feature addresses: [ ]
### Success condition: [ ]
### What it must not break: [ ]

## F4. Confirmed Scope
### What is in scope: [ ]
### What is out of scope: [ ]

## F5. Truth Status
### Confirmed: [ ]
### Inferred: [ ]
### Open: [ ]

## F6. Lacunae
### Critical blocking: [ ]
### Important non-blocking: [ ]

## F7. Readiness Posture
### Ready for implementation? [Yes / No / Conditional]
### Next step: [ ]

## F8. Feature Summary
A concise statement of what this feature is, what it must do, and what must be preserved.

[ ]

---

# CHANGE PLAN (Refactoring)

Used for the Change Path — structural improvement without behavior change.

## C1. Change Header
### Change Name: [ ]
### Codebase Area: [ ]
### Date: [ ]

## C2. Change Identity
### What will change: [ ]
### What will stay the same: [ ]
### Why the change is needed: [ ]

## C3. Current State
### Current structure: [ ]
### Why it is the way it is: [ ]
### What is problematic about it: [ ]

## C4. Impact Analysis
### What modules are affected: [ ]
### What dependencies change: [ ]
### What tests need to change: [ ]
### What behavior must be preserved: [ ]

## C5. Truth Status
### Confirmed: [ ]
### Inferred: [ ]
### Open: [ ]

## C6. Risks
### What could go wrong: [ ]
### How risks are mitigated: [ ]

## C7. Verification Approach
### How the change will be verified: [ ]

## C8. Change Summary
A concise statement of what changes, why, what is preserved, and how it is verified.

[ ]

---

# FIX PLAN (Bugfixes)

Used for the Fix Path — correcting incorrect behavior.

## B1. Fix Header
### Bug identifier: [ ]
### Severity: [Critical / Important / Minor]
### Date: [ ]

## B2. Bug Identity
### Expected behavior: [ ]
### Actual behavior: [ ]
### Reproduction steps: [ ]

## B3. Root Cause
### Where the bug originates: [ ]
### What the actual defect is: [ ]
### Whether it is local or structural: [ ]

## B4. Fix Approach
### What the fix is: [ ]
### Why it addresses the root cause: [ ]
### What it must not break: [ ]

## B5. Verification
### How the fix will be verified: [ ]
### Regression tests: [ ]

## B6. Fix Summary
A concise statement of the bug, the root cause, the fix, and the verification.

[ ]

---

# TASK BRIEF (Small Tasks)

Used for the Light Path — small implementation work.

## T1. Task Header
### Task name: [ ]
### Date: [ ]

## T2. Task Definition
### What to do: [ ]
### Constraints: [ ]
### Success criteria: [ ]

## T3. Task Notes
### What to watch out for: [ ]
### Assumptions: [ ]

## T4. Task Summary
A concise statement of what to do and what success looks like.

[ ]

---

## Next File

Continue to:

`13_PROJECT_SESSION_TEMPLATE.md`