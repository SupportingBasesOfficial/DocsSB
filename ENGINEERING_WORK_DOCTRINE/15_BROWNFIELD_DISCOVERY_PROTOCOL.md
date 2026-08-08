# BROWNFIELD DISCOVERY PROTOCOL

## Purpose of This File

This file defines the official protocol for discovering and understanding existing systems under the Engineering Work Doctrine.

Brownfield discovery is used whenever work involves an existing codebase — features, refactoring, bugfixes, or any task that modifies something that already exists. It is the counterpart to greenfield discovery (defined in `04_DISCOVERY_PROTOCOL.md`).

The purpose of brownfield discovery is not to re-discover the project from scratch. It is to understand the existing system's structure, conventions, constraints, and integration points well enough to make changes safely and coherently.

---

## When Brownfield Discovery Is Used

Brownfield discovery is used in:
- **Feature Path** — Stage 1 (Context Discovery)
- **Change Path** — Stage 1 (Codebase Analysis)
- **Fix Path** — Stage 1 (Problem Discovery)
- **Light Path** — Stage 1 (Task Discovery, when the task involves existing code)

The depth of brownfield discovery scales with the work type:
- **Feature**: Full context discovery (architecture, conventions, integration points, constraints)
- **Refactoring**: Deep structural analysis (current architecture, dependencies, coupling, patterns)
- **Bugfix**: Focused discovery (relevant code, error context, reproduction path)
- **Task**: Quick scan (relevant file, surrounding context, conventions)

> **Operational State Note:** Brownfield discovery depth also scales with Operational State. In Stable state, full discovery is required. In Formative state, discovery may be lighter. In Exploratory state, discovery is minimal or skipped. See `21_OPERATIONAL_STATES.md`.

> **Mega-tech Brownfield Discovery:** In Stable state, brownfield discovery must also surface the existing mega-tech landscape: current testing strategy and test infrastructure (`23_TESTING_STRATEGY_PROTOCOL.md`), existing ADRs and architectural decisions (`24_ARCHITECTURE_DECISION_RECORDS.md`), current observability setup (logs, metrics, traces — `25_OBSERVABILITY_PROTOCOL.md`), existing security measures and review level (`26_SECURITY_REVIEW_PROTOCOL.md`), known technical debt (`27_TECHNICAL_DEBT_PROTOCOL.md`), current dependencies and their status (`28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`), existing documentation (`29_DOCUMENTATION_PROTOCOL.md`), incident response procedures (`30_INCIDENT_RESPONSE_PROTOCOL.md`), quality gates and their enforcement (`31_QUALITY_GATES.md`), API surfaces and governance (`32_API_GOVERNANCE_PROTOCOL.md`), data classification and governance (`33_DATA_GOVERNANCE_PROTOCOL.md`), and success metrics (`34_METRICS_FEEDBACK_LOOP.md`). Without understanding the existing mega-tech landscape, new work cannot integrate safely.

---

## Brownfield Discovery Domains

### A — System Architecture

Understand the overall shape of the existing system:
- What type of system is this? (web app, API, CLI, library, service, etc.)
- What is the high-level architecture? (monolith, microservices, modular, layered, etc.)
- What are the major components and how do they relate?
- What is the entry point(s) of the system?
- What frameworks or libraries are in use?

### B — Code Conventions

Understand how the codebase is organized and written:
- What language(s) and version(s) are used?
- What is the naming convention? (files, functions, classes, variables)
- What is the file/directory structure pattern?
- What is the testing convention? (framework, location, naming)
- What is the documentation convention?
- What is the error handling pattern?
- What is the logging pattern?

### C — Integration Points

Understand where the work must connect:
- What modules or files will the work touch?
- What interfaces or APIs must be respected?
- What data structures or models are involved?
- What dependencies will be affected?
- What external systems or services are involved?

### D — Constraints

Understand what must not be broken:
- What behavior must be preserved?
- What backward compatibility is required?
- What performance constraints exist?
- What security constraints exist?
- What deployment constraints exist?
- What environment constraints exist?

### E — Risk Areas

Understand where things could go wrong:
- What is the test coverage in the affected area?
- What is the coupling complexity?
- What are the known issues or technical debt?
- What areas are fragile or poorly understood?
- What could break if the change is wrong?

### F — Change Context (for bugfixes and features)

Understand the specific change context:
- What is the current behavior?
- What is the expected behavior?
- When did the current behavior start? (for bugfixes)
- What conditions trigger the issue? (for bugfixes)
- What should the new behavior be? (for features)
- How does this fit into existing user flows?

---

## Brownfield Discovery Procedure

### Step 1 — Scope the Discovery
Determine how deep the discovery needs to go based on the work type:
- Full context (features, refactoring): All domains A-F
- Focused (bugfixes): Domains C, D, F + relevant parts of A, B
- Quick scan (small tasks): Domains C, D + relevant parts of B

### Step 2 — Explore the Codebase
Read the relevant code, configuration, and documentation:
- Start with the entry point or the area mentioned in the request
- Follow dependencies to understand the connection graph
- Read tests to understand expected behavior
- Read configuration to understand constraints
- Read documentation to understand intent

### Step 3 — Map the Architecture
Create an internal map of:
- The components involved
- The data flow
- The control flow
- The dependency graph
- The integration points

### Step 4 — Identify Constraints
Explicitly identify:
- What must not change
- What must be preserved
- What backward compatibility is needed
- What risks exist

### Step 5 — Document Findings
Organize the discovery output into:
- System context (what the existing system is and how it works)
- Change context (what specifically needs to change and why)
- Constraint context (what must be respected)
- Risk context (what could go wrong)

### Step 6 — Assess Readiness to Proceed
Determine whether enough is understood to proceed to consolidation:
- Is the existing architecture understood?
- Are the integration points clear?
- Are the constraints known?
- Are the risks identified?

If not, continue discovery. If yes, proceed to consolidation.

---

## Brownfield Discovery Principles

### Principle 1 — Respect What Exists
The existing system has reasons for being the way it is. Before changing anything, understand why it is the way it is. Do not assume the existing structure is wrong just because it is unfamiliar.

### Principle 2 — Do Not Re-Discover What Is Already Known
If the system has documentation, architecture descriptions, or README files, use them. Do not re-derive from code what is already written. But verify that the documentation matches the code — documentation can be stale.

### Principle 3 — Proportional Depth
Brownfield discovery depth must match the work type. A bugfix does not require a full architecture review. A refactoring does. Apply the Proportionality Principle.

### Principle 4 — Verify, Do Not Assume
When reading code, verify your understanding. Do not assume that a function does what its name suggests — read the implementation. Do not assume that a configuration is current — check the actual values. Assumptions in brownfield work are especially dangerous because they build on existing complexity.

### Principle 5 — Map Before Cutting
Before making any change to existing code, have a mental map of:
- What the change will touch
- What the change will affect indirectly
- What might break
- How to verify that nothing broke

This is the brownfield equivalent of "discovery before construction."

---

## Brownfield Discovery Output

The output of brownfield discovery should include:

### System Context
- System type and architecture summary
- Relevant components and their relationships
- Key conventions and patterns

### Change Context
- What specifically will be changed
- Why it needs to change
- What the expected outcome is

### Constraint Context
- What must be preserved
- What backward compatibility is needed
- What performance/security/deployment constraints apply

### Risk Context
- What could go wrong
- What is fragile or poorly tested
- What needs careful handling

### Lacuna Context
- What is not yet understood about the existing system
- What assumptions are being made
- What needs verification before proceeding

---

## Brownfield Discovery Success Condition

Brownfield discovery is functioning correctly when:
- the existing system's architecture is understood before changes are proposed
- the change context is clear (what changes, why, and what the outcome should be)
- constraints are explicitly identified (what must not break)
- risks are explicitly identified (what could go wrong)
- the depth of discovery matches the complexity of the work
- assumptions about the existing system are verified, not assumed
- the AI can explain why the existing system is the way it is before proposing changes

That is the official brownfield discovery success condition.

---

## Next File

Continue to:

`16_ANTI_PATTERNS.md`
