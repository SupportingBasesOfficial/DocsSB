# DOCUMENTATION PROTOCOL

## Purpose of This File

The Engineering Work Doctrine produces Work Agreements, Rigid Payloads, and ADRs. These are work-item artifacts — they capture decisions, changes, and rationale for a specific unit of work. But the doctrine also needs to govern **living documentation** — documentation that survives beyond individual work items and describes the system as it exists over time.

Mega-tech companies maintain documentation that outlives the code it describes. Code is rewritten, refactored, replaced. Documentation that captures the system's architecture, APIs, operational procedures, and onboarding path is the institutional memory that allows the system to survive turnover — of people and of codebases.

This file defines the documentation protocol of the Engineering Work Doctrine: what documentation exists, when it is required, what quality it must meet, and how it connects to the other doctrine artifacts.

---

## Documentation Types

The doctrine recognizes the following documentation types:

1. **Architecture documentation** — Describes the system at a structural level. Includes system overview, component diagram, data flow, and deployment topology. This is the map that allows a new contributor — human or AI — to navigate the system without reverse-engineering it from code.

2. **API documentation** — Describes the system's interfaces. Includes endpoint specs, request/response schemas, authentication, error codes, and examples. This is the contract that consumers of the system depend on.

3. **Runbooks** — Describes operational procedures for common tasks: deploy, rollback, scale, debug, incident response. This is the manual that allows the system to be operated without tribal knowledge.

4. **Onboarding documentation** — Describes how to set up, run, test, and contribute to the system. This is the entry point for any new contributor. If onboarding documentation is missing or wrong, the cost of every new contributor increases.

5. **Decision records** — ADRs. See `24_ARCHITECTURE_DECISION_RECORDS.md`. These are documentation of decisions, not of the system itself, but they are part of the documentation set.

6. **Work State Files** — Current state of work items. See `13_PROJECT_SESSION_TEMPLATE.md`. These are transient documentation that exists during work and is archived when work completes.

---

## Documentation Requirements by Work Type

Documentation requirements scale with work type, like all doctrine protocols:

| Work Type | Documentation Requirements |
|---|---|
| Project | architecture docs + API docs + runbooks + onboarding docs — full documentation set created |
| Feature | update relevant docs — API docs if new endpoints, runbooks if new operational procedures, architecture docs if new components |
| Refactoring | update architecture docs if structure changed — the docs must reflect the new structure, not the old |
| Bugfix | update runbooks if the fix changes operational behavior — e.g., a new recovery step, a changed rollback procedure |
| Task | minimal — update inline docs (code comments) if needed; no standalone documentation required |
| Question | none |

---

## Documentation Requirements by Operational State

The documentation protocol scales with the Operational State, like all doctrine protocols:

1. **Exploratory** — Documentation is not required. Exploratory work is throwaway by definition. Writing architecture docs for a prototype that may be discarded is ceremony that kills exploration. If the exploration is being captured for future use, notes may be kept — but they are not doctrine documentation.

2. **Formative** — Documentation is required when committing. The code is taking shape, and the documentation should track it. Architecture documentation is required when the shape of the system is found — i.e., when the structure is stable enough to describe, even if details are still evolving. The bar is "docs exist for committed code," not "docs are complete and polished."

3. **Stable** — Full documentation is required and must be kept up to date. Stable work is production-grade. Every documentation type required by the work type must exist, be accurate, and be maintained. Documentation drift in Stable state is a defect — it is documentation debt (see below).

This scaling prevents two failure modes:

1. Requiring documentation in Exploratory — kills exploration with ceremony
2. Not requiring documentation in Stable — leaves the system undocumented when it matters most

---

## Documentation Quality Standards

All doctrine documentation must meet these quality standards:

1. **Accurate** — Docs match the code. Outdated documentation is worse than no documentation, because it actively misleads. A reader who trusts outdated docs makes decisions based on a system that no longer exists. If docs cannot be kept accurate, they should be marked as stale or removed.

2. **Discoverable** — Docs are easy to find. They live in a known location, are linked from the README, and are organized so that a new contributor can locate what they need without asking. Documentation that cannot be found does not exist.

3. **Readable** — Docs are clear, concise, and well-structured. They are written for the reader, not for the writer. They use consistent formatting, plain language, and logical organization. A doc that is technically accurate but unreadable is functionally useless.

4. **Maintainable** — Docs are easy to update. They are not so detailed that they are always outdated, nor so sparse that they convey nothing. The level of detail is calibrated to what a reader needs to understand the system, not to exhaustively describe every implementation detail. If a doc is hard to update, it will go stale.

5. **Versioned** — Docs are versioned with the code, in the same repository. Documentation that lives outside the repo drifts from the code it describes. When code changes, the docs change in the same commit, in the same work item, in the same Rigid Payload.

---

## Documentation and the Rigid Payload

The Rigid Payload's **Alterações** section must state what documentation was created or updated for this work item.

This is not optional. The Rigid Payload captures what changed — and documentation is part of what changes. A work item that modifies code but does not update documentation has made an incomplete change. The Alterações section must explicitly list:

- Which documentation files were created or updated
- What sections were added, modified, or removed
- Why the documentation change was needed

A Rigid Payload that lists code changes but no documentation changes is either (a) a work item that genuinely required no documentation updates, or (b) a work item with documentation debt. The reviewer must determine which.

---

## Documentation Debt

Outdated documentation is **documentation debt**. It is a form of technical debt (see `27_TECHNICAL_DEBT_PROTOCOL.md`) and is governed by the same principles:

- When code changes, documentation must be updated in the same work item. Documentation updates are not a separate task to be done "later" — later never comes, and the docs go stale.
- Documentation debt accumulates silently. Unlike code debt, it does not cause test failures or build breaks. It is discovered when someone trusts the docs and is misled.
- Documentation debt must be tracked. If documentation cannot be updated in the current work item, the debt must be recorded — not silently ignored.
- Documentation debt in Stable state is a defect. Stable systems must have accurate documentation. Documentation drift in a production system is a liability.

The rule is simple: **if you change the code, you change the docs. In the same work item.**

---

## README Requirements

Every project in Stable state must have a README. The README is the entry point to the project — it is the first thing a new contributor reads, and it is the hub from which all other documentation is discovered.

The README must include:

1. **What the project is** — a clear, concise description of the project's purpose and scope
2. **How to set it up** — prerequisites, dependencies, environment setup steps
3. **How to run it** — commands and configuration for running the system locally
4. **How to test it** — commands for running the test suite, and what tests exist
5. **How to deploy it** — deployment process, or a link to the deployment runbook
6. **Where to find architecture docs** — link to the architecture documentation
7. **Where to find runbooks** — link to the runbook directory or index
8. **How to contribute** — contribution process, conventions, and expectations

A README that is missing any of these sections is incomplete. A README that links to documentation that does not exist is worse than no README — it creates false confidence.

---

## Documentation Anti-Patterns

The following are documentation anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Stale documentation** — documentation that doesn't match the code. The code says one thing, the docs say another. Stale docs are worse than no docs because they mislead.
- **Documentation as afterthought** — documentation written after the work is "done," rushed, and incomplete. In Stable state, documentation is written with the code.
- **README without quickstart** — a README that describes the project but doesn't tell the reader how to run it. A README without a quickstart is a description, not documentation.
- **No API documentation** — public APIs without documentation. Consumers must read the source to understand the interface. In Stable state, public APIs are documented.
- **Documentation that doesn't explain why** — documentation that describes what the code does but not why. The reader knows the behavior but not the reasoning.
- **No architecture diagram** — a system with no visual representation of its components and their relationships. Architecture is explained in prose that no one reads.
- **No decision records** — significant decisions made without ADRs. The team doesn't know why a decision was made, and can't evaluate it when circumstances change.

---

## Documentation and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that the final state is documented — architecture, decisions, constraints. No work enters Stable state with stale or missing documentation.

---

## Protocol Success Condition

The documentation protocol has been applied successfully when:

1. Every Stable project has accurate, discoverable, and maintained architecture documentation, API documentation, runbooks, and onboarding documentation.
2. Every Stable project has a README that includes all required sections.
3. Documentation updates are recorded in the Rigid Payload's Alterações section for every work item that changes code.
4. Documentation drift is treated as documentation debt and is tracked, not ignored.
5. The depth of documentation matches the Operational State — none required in Exploratory, tracked in Formative, complete and maintained in Stable.

That is the official success condition of the documentation protocol.

**Anti-pattern:** See ANTI-PATTERN 37 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.8 in `08_DECISION_RULES.md`.

---

## Next File

The next file in the doctrine is `30_INCIDENT_RESPONSE_PROTOCOL.md`.
