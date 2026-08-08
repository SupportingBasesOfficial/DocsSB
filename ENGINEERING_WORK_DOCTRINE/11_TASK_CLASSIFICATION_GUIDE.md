# TASK CLASSIFICATION GUIDE

## Purpose of This File

This file defines the official protocol for classifying work requests under the Engineering Work Doctrine.

Task classification is the first action the AI takes after receiving any work request. It determines which lifecycle path the work will follow, how deep the process will be, and what form of work agreement is required.

Classification exists because not all work is the same. Applying a heavy project-birth process to a trivial question wastes time. Applying a trivial process to a complex new project creates shallow foundations. Classification ensures the right process for the right work.

---

## When Classification Happens

Classification happens at Stage 0 — the moment a work request arrives, before any discovery, consolidation, or delivery begins.

The AI must classify the work before doing anything else. The only exception is when the request is so ambiguous that classification itself requires clarification — in which case the AI asks a brief classification question first.

---

## Classification Dimensions

The AI must evaluate the work request across these dimensions:

### 1. Origin
- **Greenfield**: Something new is being created from scratch
- **Brownfield**: Something existing is being modified, fixed, or improved

### 2. Scope
- **System-wide**: Affects the entire system or architecture
- **Subsystem**: Affects a major component or module
- **Local**: Affects a single file, function, or configuration
- **Informational**: No system impact — the user wants knowledge or advice

### 3. Risk
- **High**: Wrong execution could cause data loss, security breach, or major downtime
- **Medium**: Wrong execution could cause bugs or require rework
- **Low**: Wrong execution is easily reversible
- **None**: No execution risk — informational only

### 4. Complexity
- **Multi-dimensional**: Many aspects need to be understood (users, data, flows, governance, scale)
- **Moderate**: Several aspects need to be understood
- **Low**: One or two aspects need to be understood
- **Trivial**: The request is self-contained and obvious

### 5. Ambiguity
- **High**: What is needed is largely unclear
- **Moderate**: What is needed is partially clear
- **Low**: What is needed is mostly clear
- **None**: What is needed is completely clear

---

## Task Types and Selection Criteria

### Project → Full Lifecycle

**Select when ALL of the following are true:**
- The work is greenfield (new system, application, tool, or platform) OR a major restructuring of an existing system that creates a fundamentally new architecture
- The scope is system-wide or major subsystem
- Multiple dimensions need to be understood (users, data, flows, governance, scale)
- Ambiguity is moderate to high
- The work will result in a new engineering identity

**Examples:**
- "I want to build an app for managing inventory"
- "I need a platform for customer feedback"
- "I want to create a tool that automates my workflow"
- "We need a new system for tracking orders"
- "Convert our monolith to microservices" (brownfield project — major restructuring, see note below)

**Brownfield Project Note:**
When a project involves major restructuring of an existing system (e.g., monolith-to-microservices, platform re-architecture, complete data model overhaul), it is classified as a Project, not a Refactoring. The distinction is:
- **Refactoring** improves structure without changing the architectural identity
- **Brownfield Project** creates a new architectural identity within an existing codebase

Brownfield projects use the Full Lifecycle but combine greenfield discovery (for the new architecture) with brownfield discovery (for understanding the existing system that must be migrated). See `04_DISCOVERY_PROTOCOL.md` and `15_BROWNFIELD_DISCOVERY_PROTOCOL.md`.

### Feature → Feature Path

**Select when ALL of the following are true:**
- The work is brownfield (existing system)
- The scope is a subsystem or major component
- The work adds new capability (not fixing broken behavior)
- The existing system's constraints must be respected
- Ambiguity is moderate

**Examples:**
- "Add a reporting dashboard to the existing app"
- "Add multi-tenant support to the platform"
- "Add OAuth authentication to the existing API"
- "Add export to PDF in the existing tool"

### Refactoring → Change Path

**Select when ALL of the following are true:**
- The work is brownfield
- The work improves structure without changing behavior
- The scope is a subsystem or larger
- Understanding the current structure is essential
- Impact analysis is needed

**Examples:**
- "Refactor the authentication module to use a cleaner pattern"
- "Extract the business logic from the controllers"
- "Migrate from a monolith to a modular architecture"
- "Clean up the code that has become hard to maintain"

### Bugfix → Fix Path

**Select when ALL of the following are true:**
- The work is brownfield
- The work corrects incorrect behavior
- The root cause must be identified (not just the symptom)
- Verification is needed to confirm the fix

**Examples:**
- "The login page crashes when I enter a special character"
- "The report shows wrong totals for Q3"
- "The API returns 500 errors under heavy load"
- "Data is being saved with the wrong timestamp"

### Task → Light Path

**Select when ALL of the following are true:**
- The work is small in scope (single file, function, or configuration)
- The complexity is low
- The ambiguity is low
- The risk is low
- The work does not require understanding multiple system dimensions

**Examples:**
- "Write a script to convert CSV to JSON"
- "Change the database connection string in the config"
- "Add a new field to the user model"
- "Write a function to validate email addresses"

### Question → Direct Path

**Select when ALL of the following are true:**
- The work is informational
- No implementation is requested
- The user wants knowledge, analysis, opinion, or explanation
- No system impact

**Examples:**
- "What's the best way to structure a multi-tenant database?"
- "Should I use SQL or NoSQL for this use case?"
- "Explain how JWT authentication works"
- "What are the trade-offs between microservices and monolith?"

---

## Classification Procedure

### Step 1 — Read the Request
Read the user's request carefully. Do not skim. Understand what is being asked before classifying.

### Step 2 — Evaluate Dimensions
Assess the request across all five dimensions: origin, scope, risk, complexity, ambiguity.

### Step 3 — Match to Task Type
Match the dimension assessment to the task type criteria above.

### Step 4 — Select Lifecycle Path
Select the lifecycle path corresponding to the task type.

### Step 5 — Output Classification
State the classification explicitly:
- The identified task type
- The selected lifecycle path
- A brief justification (1-2 sentences)
- The expected process depth

### Step 6 — Begin the Path
Transition to Stage 1 of the selected lifecycle path.

---

## Classification Edge Cases

### Ambiguous Classification
If the work could be two types (e.g., "is this a feature or a small project?"), default to the heavier path. It is always safer to over-understand than to under-understand.

### Misclassification Discovery
If, during any stage, the AI discovers that the work is more complex or different than initially classified, it must:
1. Stop the current path
2. Re-classify the work
3. State the re-classification explicitly
4. Transition to the appropriate path

Silent path continuation when the work type has changed is a doctrinal failure.

### Compound Requests
If a single request contains multiple work types (e.g., "build a new module and fix the bug in the existing one"), classify each part separately and execute each on its appropriate path.

### Escalation
If a task initially classified as small reveals hidden complexity during discovery, the AI must escalate to a heavier path. For example, a "simple bugfix" that reveals a systemic data integrity problem must be re-classified as a project or feature.

### De-escalation
If a task initially classified as heavy turns out to be simpler than expected, the AI may de-escalate to a lighter path. For example, a "new project" that turns out to be a minor script may be re-classified as a task. This must be stated explicitly.

---

## Classification Output Format

The AI must output the classification in this format:

```
Work Type: [Project | Feature | Refactoring | Bugfix | Task | Question]
Lifecycle Path: [Full | Feature | Change | Fix | Light | Direct]
Justification: [1-2 sentences explaining why this type was selected]
Process Depth: [Maximum | High | Medium | Low | Minimal]
```

This output makes the classification explicit and auditable. It prevents silent classification and ensures the user understands what process to expect.

---

## Classification Success Condition

Classification is functioning correctly when:
- every work request is classified before process begins
- the classification is explicit and justified
- the selected path matches the actual complexity of the work
- misclassifications are detected and corrected promptly
- small tasks receive light process
- large tasks receive heavy process
- compound requests are decomposed into separate classifications
- the user understands what process to expect

That is the official classification success condition.

---

## Operational State Classification

In addition to classifying the Work Type, the AI must classify the **Operational State** of each work item. The Operational State determines how strict the doctrine's rules are, based on the preciousness and reversibility of the output.

### The Three States

| State | When | Output is |
|---|---|---|
| Exploratory | Spikes, prototypes, feasibility investigations | Throwaway |
| Formative | Active development, iterating on shape | Being shaped — history not yet valuable |
| Stable | Production, pre-production hardening, live systems | Precious — full doctrine applies |

### How to Determine State

1. Is the system live? → Stable
2. Does the system have real users or real data? → Stable
3. Is the output throwaway (spike, prototype)? → Exploratory
4. Is the shape still being discovered? → Formative
5. Is the system being hardened for production? → Stable
6. If unclear → default to Stable (safest assumption)

### State Is Per-Item, Not Per-Project

A project can have work items in different states:
- Core module: Stable (live, full process)
- New feature: Formative (being built, iterating)
- Spike for future capability: Exploratory (throwaway)

### Declaration Format

The state should be declared alongside the work type:

> "This work is classified as: Feature (work type) in Formative state (operational state)."

### Default: Stable

When the state cannot be determined, default to Stable. The user may declare a lighter state, but the AI must not assume it.

See `21_OPERATIONAL_STATES.md` for the full state definitions, transitions, and rule mappings.

### Mega-tech Protocol Activation

The Operational State determines which mega-tech protocols (files 23-34) are activated:

| State | Mega-tech Protocols |
|---|---|
| Exploratory | Skipped — output is throwaway |
| Formative | Lighter — applied when committing (testing, documentation, debt tracking) |
| Stable | Full — all 12 protocols apply: testing strategy (`23`), ADRs (`24`), observability (`25`), security review (`26`), technical debt (`27`), dependency management (`28`), documentation (`29`), incident response (`30`), quality gates (`31`), API governance (`32`), data governance (`33`), metrics & feedback (`34`) |

When classifying work as Stable, the AI must be aware that classification activates the full mega-tech stack. This is not optional — it is the definition of "production-ready" in this doctrine.

---

## Next File

Continue to:

`12_TEMPLATE_WORK_AGREEMENT.md`
