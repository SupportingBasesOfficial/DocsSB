# TECHNICAL DEBT PROTOCOL

## Purpose of This File

This file defines the official Technical Debt Protocol of the Engineering Work Doctrine.

Its purpose is to ensure that technical debt is **tracked explicitly, classified by severity, owned by a responsible party, and paid off on a defined plan**.

Technical debt is inevitable in any real system. The doctrine has 42 anti-patterns that prevent debt creation, but prevention is not enough. Debt already exists, and debt is sometimes intentionally incurred to meet a deadline. A doctrine that only prevents debt but does not manage existing debt is incomplete.

This is standard practice at mega-tech companies. Technical debt is tracked explicitly with an owner, a severity, and a payoff plan. Debt is not hidden. Debt is not ignored. Debt is recorded, prioritized, and paid down deliberately. The doctrine adopts the same standard.

This file defines:
- what types of technical debt exist
- the difference between intentional and unintentional debt
- how debt is tracked in a Debt Register
- how debt is classified by severity
- how debt management scales with operational state
- how debt is handled at the Consolidation Moment
- how debt is recorded in the Rigid Payload
- how debt is paid off
- when the protocol has been applied successfully

---

## Technical Debt Types

Technical debt is not a single thing. It takes several forms, each with different causes and different payoff strategies. The doctrine recognizes seven types.

- **Code debt** — poor code quality, duplication, excessive complexity, missing abstractions, unclear naming, long functions, deep nesting. The code works but is hard to read, hard to change, and easy to break.
- **Design debt** — poor architecture, tight coupling, missing layers, wrong patterns, circular dependencies, god objects. The structure of the system resists change. Fixing one thing breaks another.
- **Test debt** — missing tests, low coverage, flaky tests, no integration or end-to-end tests, tests that do not assert the right things. The system cannot be changed with confidence because the safety net is broken or absent.
- **Documentation debt** — missing docs, outdated docs, missing ADRs, missing onboarding guides, code with no comments where comments are needed. Knowledge is not captured and is lost when people move on.
- **Dependency debt** — outdated dependencies, pinned old versions, known security vulnerabilities in dependencies, abandoned dependencies, duplicate dependencies. The system is tied to versions that are no longer maintained or safe.
- **Infrastructure debt** — outdated tooling, missing CI/CD, missing observability, manual deployment, no staging environment, missing backup strategy. The system runs but cannot be operated, deployed, or observed reliably.
- **Knowledge debt** — concentrated knowledge in one person, missing onboarding docs, undocumented domain logic, tribal knowledge that is not written down. The system is a single point of failure at the human level.

---

## Intentional vs Unintentional Debt

Not all debt is the same. The doctrine distinguishes between debt that is deliberately incurred and debt that accumulates through poor practice.

### Intentional Debt

Intentional debt is debt deliberately incurred to meet a deadline, ship a feature, or respond to an incident. The team knows the debt exists, understands the tradeoff, and has a documented plan to pay it off.

Intentional debt is **acceptable in Formative state with a note**. The note must record what was deferred, why it was deferred, and when it will be addressed. Intentional debt without a note is unintentional debt.

### Unintentional Debt

Unintentional debt is debt accumulated through poor practice, not recognized until later. It builds up silently. It is discovered during review, during debugging, or when a change that should be simple turns out to be hard.

This is what the anti-patterns prevent. The 42 anti-patterns exist to stop unintentional debt from being created in the first place. When anti-patterns are violated, unintentional debt is the result.

---

## Debt Tracking

Technical debt must be tracked in a **Debt Register**. The Debt Register is the single source of truth for all known debt in the system. Debt that is not in the register does not exist as far as the doctrine is concerned — and untracked debt is the most dangerous kind.

Each entry in the Debt Register must record:

- **Debt ID** — sequential identifier (DEBT-001, DEBT-002, ...)
- **Description** — what the debt is, written clearly enough that someone unfamiliar with the work can understand it
- **Type** — code, design, test, documentation, dependency, infrastructure, knowledge
- **Severity** — critical, high, medium, low (see classification below)
- **Location** — where in the codebase the debt lives (file, module, component, system)
- **Owner** — who is responsible for paying it off (a person, a team, or a role)
- **Payoff plan** — when and how the debt will be addressed
- **Status** — open, in-progress, paid
- **Date incurred** — when the debt was created or recognized
- **Date paid** — when the debt was resolved (empty until paid)

A Debt Register entry without an owner is not a valid entry. Unowned debt is unmanaged debt.

---

## Debt Severity Classification

Debt severity determines priority. Not all debt is equally urgent. The doctrine defines four severity levels.

- **Critical** — causes or will soon cause incidents, security vulnerabilities, or data loss. This debt is actively harming the system or will do so imminently. **Must be addressed immediately.** Critical debt is a Fix Path, not a scheduled task.
- **High** — causes significant maintenance burden, slows down feature work, or has known vulnerabilities that are not yet exploitable. This debt is not causing incidents yet but is draining productivity or carrying real risk. **Should be addressed within the current quarter.**
- **Medium** — causes friction but is manageable. The team works around it. It slows things down but does not block them. **Should be addressed within the current year.**
- **Low** — minor inconvenience, not urgent. The debt is annoying but not harmful. **Address when touching the related code.** Opportunistic payoff.

---

## Debt and Operational State

Debt management depth scales with the operational state of the work. See `21_OPERATIONAL_STATES.md` for the full state definitions.

| Operational State | Debt Management Requirement |
|---|---|
| Exploratory | Debt is not tracked. Exploratory output is throwaway. Tracking debt in throwaway code is disproportionate. |
| Formative | Intentional debt is tracked with a payoff plan. Unintentional debt is expected and is cleaned during the Consolidation Moment. The system is still taking shape — some debt is part of the process. |
| Stable | All debt must be tracked in the Debt Register. Critical debt must be addressed before new features. No untracked debt is permitted. |

In Stable state, critical debt takes priority over feature work. A team that ships features while critical debt sits open is violating the doctrine.

---

## Debt and the Consolidation Moment

The Consolidation Moment (defined in `21_OPERATIONAL_STATES.md`, protocol in `05_CONSOLIDATION_PROTOCOL.md`) is the transition from Formative to Stable. It is the point where the system stops being a prototype and starts being a production system. Debt cannot drift into Stable unexamined.

The Consolidation Moment must include:

- **Review all intentional debt incurred during Formative** — every debt item created during the Formative period is examined. Is it still relevant? Is it still accurate? Has it gotten worse?
- **Pay off or explicitly accept each debt item** — each item is either resolved or formally accepted with a documented reason and a payoff plan. Silent acceptance is not permitted.
- **Enter remaining debt into the Debt Register** — any debt that survives the Consolidation Moment is entered into the Debt Register with full metadata (owner, severity, payoff plan).
- **No untracked debt may survive into Stable** — if debt exists and is not in the register, the Consolidation Moment is not complete. The transition to Stable is blocked.

The Consolidation Moment is the last chance to clean debt before the full doctrine applies. Debt that survives into Stable is subject to the full tracking and payoff protocol.

---

## Debt and the Rigid Payload

If a work item intentionally incurs debt, the Rigid Payload (defined in `09_OUTPUT_QUALITY_STANDARD.md`) must record it. The Alterações section of the Rigid Payload must note:

- **What debt was incurred** — a clear description of the debt, what was deferred or compromised
- **Why it was incurred** — the justification. What deadline, constraint, or tradeoff made this debt the right choice at this time
- **When it will be paid off** — the expected payoff timeframe or the trigger that will initiate payoff
- **Debt ID in the Debt Register** — the identifier assigned to this debt in the Debt Register

A Rigid Payload that incurs debt without recording it is incomplete. The work cannot be declared 100% complete. Unrecorded intentional debt becomes unintentional debt, and unintentional debt is what the anti-patterns exist to prevent.

---

## Technical Debt Anti-Patterns

The following are technical debt anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Untracked intentional debt** — debt that was intentionally incurred to meet a deadline but never recorded. It becomes unintentional debt — no one knows it exists, no one plans to pay it off.
- **Debt as excuse** — labeling poor work as "technical debt" to avoid doing it properly. True technical debt is intentional, tracked, and has a payoff plan. Poor work is just poor work.
- **Debt that never gets paid** — debt that is recorded but never addressed. The Debt Register grows, but no items are ever resolved. The register becomes a graveyard.
- **Debt without severity** — all debt is treated equally. Critical debt (blocks future work, causes bugs) is lumped with low debt (cosmetic, minor inconvenience). Prioritization is impossible.
- **Paying debt without tests** — refactoring to pay off debt without characterization tests first. The refactoring may introduce regressions, turning debt resolution into bug creation.
- **Accumulating debt in Stable state** — incurring new intentional debt in Stable state without explicit user approval. Stable state is production-grade; new debt requires justification.

---

## Debt Payoff Protocol

Debt does not pay itself off. It must be addressed deliberately through the appropriate work path.

- **Debt payoff is a Refactoring work type** — paying off debt is a Change Path (see `11_TASK_CLASSIFICATION_GUIDE.md`). It is not a feature, not a bugfix, and not a task. It is a deliberate change to the structure of the system without changing its behavior.
- **Critical debt: immediate Fix Path** — critical debt is treated as an incident or an imminent incident. It follows the Fix Path, not the Change Path. It is addressed now, not scheduled.
- **High debt: scheduled Change Path in current quarter** — high debt is scheduled as a Refactoring work item within the current quarter. It is planned, scoped, and executed deliberately.
- **Medium/Low debt: opportunistic** — medium and low debt are addressed when touching the related code. When a work item touches a file or module that carries medium or low debt, that debt should be paid off as part of the same work. This is the boy scout rule: leave the code better than you found it.

---

## Protocol Success Condition

The Technical Debt Protocol has been applied successfully when:

- all debt in Stable state is tracked in the Debt Register
- every tracked debt item has a type, severity, owner, and payoff plan
- critical debt is addressed immediately, before new feature work
- intentional debt incurred during Formative is reviewed and either paid off or formally accepted at the Consolidation Moment
- no untracked debt survives the Consolidation Moment into Stable
- work items that incur debt record it in the Rigid Payload with a Debt Register ID

That is the official success condition of the Technical Debt Protocol.

The Technical Debt Gate (see `31_QUALITY_GATES.md`) enforces that no untracked debt survives into Stable state — the gate blocks stage transitions when debt is not recorded in the Debt Register with the required metadata.

**Anti-pattern:** See ANTI-PATTERN 35 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.6 in `08_DECISION_RULES.md`.

---

## Next File

Continue to:

`28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`
