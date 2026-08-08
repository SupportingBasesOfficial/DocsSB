# ENFORCEMENT LAYER

## Purpose of This File

This file defines the official enforcement layer of the Engineering Work Doctrine.

The doctrine governs **how to approach work** — classification, discovery, consolidation, agreement, readiness, delivery. But governance alone is not enough. Governance tells the AI what to do. Enforcement guarantees that what was done is correct.

This file exists because a doctrine without enforcement is a constitution without police. It works when the AI cooperates. It fails when the AI does not.

The enforcement layer closes that gap. It defines how the doctrine's quality standards become **mechanically verifiable** — not through hope, but through deterministic checks that block incorrect work from passing.

---

## The Five-Layer Architecture

The Engineering Work Doctrine operates within a five-layer architecture. Each layer answers a different question:

```
┌─────────────────────────────────────────────────────────┐
│  LAYER 1 — GOVERNANCE COGNITIVA (this doctrine)         │
│  "What work is this? How should it be approached?"      │
│  Files: 00-19 of the Engineering Work Doctrine          │
├─────────────────────────────────────────────────────────┤
│  LAYER 2 — EXECUTION FLOW                               │
│  "How to execute this work with mastery?"               │
│  File: 07_DELIVERY_PROTOCOL.md (5-stage execution flow) │
├─────────────────────────────────────────────────────────┤
│  LAYER 3 — ENFORCEMENT (files 20-22)                    │
│  "Is the work 100% correct? Prove it."                  │
│  Instruments: validators, gates, integrity protection,  │
│  operational states, discovery dimensions               │
├─────────────────────────────────────────────────────────┤
│  LAYER 4 — MEGA-TECH PROTOCOLS (files 23-34)            │
│  "Is this production-grade?"                            │
│  12 protocols scaling with operational state            │
├─────────────────────────────────────────────────────────┤
│  LAYER 5 — CONSTITUTION                                 │
│  "What are the non-negotiable rules of this project?"   │
│  Component of: 12_TEMPLATE_WORK_AGREEMENT.md            │
└─────────────────────────────────────────────────────────┘
```

No layer replaces another. Each operates at its own level. Together they cover the complete cycle from request to verified, production-grade delivery.

---

## Layer 1 — Governance Cognitive

**Question answered:** What work is this? How should it be approached?

**What it does:**
- Classifies the work type (Project, Feature, Refactoring, Bugfix, Task, Question)
- Selects the appropriate lifecycle path
- Conducts discovery (greenfield or brownfield)
- Consolidates understanding
- Forms a work agreement (tiered)
- Verifies readiness
- Initiates delivery

**What it does NOT do:**
- It does not verify that the executed work is correct
- It does not enforce quality mechanically
- It does not block incorrect work from passing

**Files:** All 20 files of the Engineering Work Doctrine (00-19).

---

## Layer 2 — Execution Flow

**Question answered:** How to execute this work with mastery?

**What it does:**
- Defines the 5-stage execution flow: ENTENDER → ESTUDAR → PLANEJAR → EXECUTAR → VERIFICAR
- Ensures understanding precedes execution
- Enforces the 80/20 principle (80% effort in understanding, 20% in execution)
- Prohibits workarounds
- Requires root cause, not symptom
- Demands the first execution be the correct one

**What it does NOT do:**
- It does not mechanically verify the output
- It does not block code that fails quality checks

**File:** `07_DELIVERY_PROTOCOL.md` (execution flow section).

---

## Layer 3 — Enforcement

**Question answered:** Is the work 100% correct? Prove it.

**What it does:**
- Runs deterministic validators against the work output
- Blocks work that does not pass 100%
- Protects immutable files from tampering (hash verification)
- Enforces quality at three gates: pre-commit, pre-push, CI
- Governs operational states (Exploratory/Formative/Stable) via `21_OPERATIONAL_STATES.md`
- Ensures discovery dimension coverage via `22_DISCOVERY_DIMENSION_PROTOCOL.md`

**What it does NOT do:**
- It does not decide what work to do (Layer 1 does that)
- It does not define how to execute (Layer 2 does that)
- It does not define mega-tech protocols (Layer 4 does that)
- It does not define project-specific rules (Layer 5 does that)

**Implementation:** Enforcement is implemented by enforcement instruments — tools that run validators, hooks, and CI checks. The doctrine defines what enforcement must do; instruments implement it.

### Enforcement Gates

| Gate | When | What happens | Bypass |
|------|------|--------------|--------|
| pre-commit | Before commit | Local validators run. Code that doesn't pass 100% is blocked. | `--no-verify` (discouraged) |
| pre-push | Before push | Deeper validators run. Code that doesn't pass 100% is blocked. | `--no-verify` (discouraged) |
| CI | On push/PR | All validators run. Code that doesn't pass 100% is blocked. | Cannot be bypassed |

### Validator Categories

The doctrine defines these validator categories. An enforcement instrument should implement them:

**Pre-commit gate (fast, local):**
1. **type-check** — compiles and types are correct
2. **lint** — follows project conventions
3. **doctrine-check** — no workarounds in Stable state, direct path, certainty markers present
4. **test** — all tests pass + critical path coverage
5. **security-scan** — SAST + dependency audit + secrets scan
6. **contract-check** — inter-module contracts respected
7. **anchor-check** — context anchors consistent
8. **tech-debt-check** — phantom imports, orphan env vars, unused deps, circular deps, `any` type, missing return types, unused exports

**Pre-push gate (deeper, local or remote):**
9. **context-drift-check** — context files haven't drifted from source code
10. **property-tests** — property-based invariants hold
11. **impact-analysis** — change blast radius within threshold
12. **schema-sync-check** — ORM models match SQL migrations
13. **api-compat-check** — API backward compatibility
14. **perf-budget-check** — N+1 queries, unpaginated reads, SELECT *, await in loop

**CI gate (complete, remote):**
15. **mutation-test** — tests detect mutations (tests are actually meaningful, not just passing)

### Proportional Enforcement

Enforcement depth scales with work type, per the Proportionality Principle:

| Work Type | Validators applied | Rationale |
|-----------|-------------------|-----------|
| Project | All 15 | New systems need full verification |
| Feature | type-check, lint, test, security-scan, contract-check, tech-debt-check, impact-analysis | New capability in existing system needs integration + quality checks |
| Refactoring | type-check, lint, test, property-tests, mutation-test | Behavior must be preserved — mutation testing is critical here |
| Bugfix | type-check, lint, test, security-scan | Fix must be correct and not introduce new issues |
| Task | type-check, lint | Small tasks need basic verification only |
| Question | None | No code to validate |

Applying all 15 validators to a question is a doctrinal failure (over-engineering). Applying only lint to a refactoring is a doctrinal failure (under-engineering — mutation testing is essential for refactoring).

### Integrity Protection

The enforcement layer protects immutable files through hash verification:

- **system-rules.md** — doctrine rules that must not be tampered with
- **tech-stack.json** — declared technology stack
- **source-of-truth.json** — declared source of truth files

SHA-256 hashes are computed and stored. Any modification is detected and blocked. This prevents silent doctrine drift through file tampering.

---

## Layer 4 — Mega-tech Protocols

**Question answered:** Is this production-grade?

**What it does:**
- Defines 12 protocols that scale with operational state (Exploratory/Formative/Stable)
- Covers testing strategy, ADRs, observability, security review, technical debt, dependency management, documentation, incident response, quality gates, API governance, data governance, metrics & feedback loop
- Mandatory in Stable state, lighter in Formative, skipped in Exploratory
- Each protocol defines work-type-specific requirements and Rigid Payload integration

**What it does NOT do:**
- It does not define the process (Layer 1 does that)
- It does not define execution flow (Layer 2 does that)
- It does not run validators (Layer 3 does that)
- It does not define project-specific rules (Layer 5 does that)

**Where it lives:** Files 23-34 of the Engineering Work Doctrine. Each protocol is a standalone file that cross-references the enforcement layer and operational states.

**The 12 protocols:**
- `23_TESTING_STRATEGY_PROTOCOL.md` — defines required test types by work type and state
- `24_ARCHITECTURE_DECISION_RECORDS.md` — records significant architectural decisions
- `25_OBSERVABILITY_PROTOCOL.md` — logs, metrics, traces, alerts, dashboards
- `26_SECURITY_REVIEW_PROTOCOL.md` — security review at 3 levels (L1/L2/L3)
- `27_TECHNICAL_DEBT_PROTOCOL.md` — 7 debt types, Debt Register, payoff plans
- `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md` — dependency evaluation, versioning, security
- `29_DOCUMENTATION_PROTOCOL.md` — living documentation by type
- `30_INCIDENT_RESPONSE_PROTOCOL.md` — SEV1-4, blameless post-mortems
- `31_QUALITY_GATES.md` — gates at every stage transition
- `32_API_GOVERNANCE_PROTOCOL.md` — naming, versioning, error handling
- `33_DATA_GOVERNANCE_PROTOCOL.md` — 4 classification levels, handling rules
- `34_METRICS_FEEDBACK_LOOP.md` — DORA metrics, doctrine metrics, feedback

The enforcement layer (Layer 3) enforces these protocols through validators and gates. See `31_QUALITY_GATES.md` for the gate definitions that check these protocols.

---

## Layer 5 — Constitution

**Question answered:** What are the non-negotiable rules of this project?

**What it does:**
- Defines project-specific invariants (rules that must always hold)
- Defines standards (language, runtime, linter, test framework)
- Defines prohibitions (what is never allowed in this project)
- Defines validation configuration (thresholds, timeouts)

**What it does NOT do:**
- It does not define the process (Layer 1 does that)
- It does not define execution flow (Layer 2 does that)
- It does not run validators (Layer 3 does that)
- It does not define mega-tech protocols (Layer 4 does that)

**Where it lives:** The Constitution is a component of the Full Work Agreement (`12_TEMPLATE_WORK_AGREEMENT.md`). Each project defines its own Constitution as part of its work agreement. The doctrine is universal; the Constitution is local.

### Constitution Structure

A Constitution contains:

**Invariantes** — rules that must always hold:
- Every function has explicit return type
- Every exported function has tests
- No `any` in TypeScript
- No `console.log` in production
- Every change passes the applicable validators
- Every function under 50 lines
- Imports organized: external → internal

**Direção** — project direction:
- Objective
- Priority (functionality > performance > aesthetics)
- Definition of done (100% of acceptance criterion)

**Padrões** — standards:
- Language
- Runtime
- Linter
- Test framework

**Proibições** — prohibitions:
- Workarounds (always resolve root cause)
- `any` in TypeScript (use `unknown` + type guard)
- `console.log` in production (use structured logger)
- Unused imports
- Functions over 50 lines
- TODO/FIXME/HACK in code
- Empty try/catch that silences errors
- Forced casts (`as any`, `as unknown as X`)
- Duplicated logic
- Abstractions used only once

**Configuração de Validação** — validation config:
- requireTests: true/false
- preCommitTimeout
- prePushTimeout
- ciTimeout
- mutationThreshold
- coverageThreshold

---

## The 100% Principle

The enforcement layer operates on a single foundational principle:

**100% is the floor, not the ceiling.**

Below 100%, work is not done. This is not aspiration. It is the minimum acceptance criterion.

This principle applies proportionally:
- For code generation: compiles + tests pass + no tech debt + meets spec + no broken dependencies
- For refactoring: identical behavior (proof of equivalence) + cleaner code + no regression
- For bugfix: root cause resolved + bug test passes + no new bugs
- For architecture: inevitable components + minimal interfaces + defined invariants
- For conceptual answer: exact + no irrelevance + no critical omission + semantically precise
- For deploy: build + tests + health check + rollback + zero downtime + observability
- For migration: schema validated + sandbox tested + safe rollback + zero data loss
- For infra as code: template validated + drift + security + cost + idempotent
- For API design: formal contract + versioning + auth + rate limiting + error codes
- For security audit: SAST + DAST + dependency + secrets + zero vulns + attack surface
- For performance: benchmark + target + regression + profiling + no bottlenecks
- For documentation: 100% APIs + executable examples + diagrams + zero ambiguity

See `09_OUTPUT_QUALITY_STANDARD.md` for the full 100% criteria table.

---

## Payload Rígido (Rigid Payload)

When the work involves implementation (projects, features, refactoring, bugfixes), the AI's output must follow the Rigid Payload format — 4 mandatory sections:

### 1. Diagnóstico (Diagnosis)
What was the problem. What was the root cause. What needed to change and why.

### 2. Alterações (Changes)
What was changed. Which files. Which functions. What was added, modified, or removed.

### 3. Enforcement
How the changes were verified. Which validators passed. What coverage was achieved. What tests were run.

### 4. Rollback
How to revert the changes if something goes wrong. What the rollback path is. What the risk areas are.

For work in Stable state that involves deployment, the Rollback section must also address:

#### Deployment Strategy
The deployment strategy must be specified:
- **Blue-green deployment** — new version deployed alongside old; traffic switched after verification
- **Canary deployment** — new version deployed to a subset of users; rolled out gradually after monitoring
- **Rolling deployment** — instances updated one at a time; system stays available throughout
- **Feature flags** — new behavior gated behind flags; can be toggled on/off without redeployment

The strategy must match the availability requirements discovered during the Discovery Dimension Protocol (see `22_DISCOVERY_DIMENSION_PROTOCOL.md`).

#### Zero-Downtime Requirements
For systems with availability requirements (SLOs/SLAs), the Rollback section must specify:
- How the deployment maintains availability (no user-visible downtime)
- Health checks that gate the deployment (automatic rollback on health check failure)
- Monitoring that detects problems during deployment
- The decision point for rollback (what metrics trigger automatic vs manual rollback)
- Data migration compatibility (schema changes must be backward-compatible during deployment)

#### Migration Safety
For work that involves data migrations:
- Migrations must be backward-compatible (old code can read new schema, new code can read old schema)
- Migrations must be reversible (each migration has a down/rollback path)
- Data integrity must be verified after migration
- Migration must be tested in a staging environment before production

The Rigid Payload is not optional for implementation work. It ensures the AI produces not just code but also the reasoning, verification, and safety net that make the code trustworthy.

For non-implementation work (questions, task briefs), the Rigid Payload does not apply.

---

## Prompt Salt

The enforcement layer includes a mechanism called Prompt Salt — a micro-anchor that re-injects critical rules into the AI's attention cycle.

Because AI attention degrades over long contexts, critical rules can be forgotten mid-session. Prompt Salt prevents this by periodically re-injecting the most important rules:

- 100% is the floor (refined by Operational State)
- No workarounds in Stable state (allowed in Exploratory/Formative with notes)
- Root cause, not symptom
- Study before execute
- Payload Rígido required for implementation in Stable state

This is not restating the doctrine. It is a lightweight attention anchor that keeps the critical rules active throughout the session.

---

## False Positive Protocol

Validators can produce false positives — a validator reports a failure that is not actually a failure. This is legitimate and must be handled with discipline, not by silent bypass.

### When a Validator Reports a False Positive

1. **Do not silently bypass.** Using `--no-verify` without explanation is Anti-Pattern 29 (Silent Bypass).

2. **Investigate the failure first.** Confirm it is actually a false positive, not a real issue being dismissed. The AI must verify:
   - is the validator configuration correct?
   - is the validator version compatible?
   - is the flagged pattern genuinely safe in this context?
   - is there a known issue with this validator for this case?

3. **Document the false positive.** If confirmed as a false positive, document:
   - which validator produced the false positive
   - what it flagged
   - why it is a false positive (not a real issue)
   - what context makes the flagged pattern safe

4. **Bypass explicitly.** The bypass must be:
   - explicit (stated in the output, not hidden)
   - justified (reason documented)
   - scoped (only the specific check, not all validators)
   - temporary (a fix should be filed with the validator or the configuration adjusted)

5. **Record in Rigid Payload.** In the Enforcement section of the Rigid Payload, state:
   - "Validator X reported failure Y"
   - "Confirmed as false positive because Z"
   - "Bypassed with explicit justification"
   - "Workaround: adjust validator configuration to exclude this pattern"

### False Positive vs. Real Issue

The distinction is critical:
- **False positive:** the validator is wrong — the code is correct
- **Real issue dismissed:** the validator is right — the AI is dismissing it to avoid work

If the AI cannot confidently distinguish, it must treat the failure as a real issue. Dismissing a real issue as a false positive is worse than investigating a false positive as a real issue.

### When in Doubt, Do Not Bypass

If the AI is not certain the failure is a false positive, it must:
- resolve the issue (fix the code so the validator passes)
- or ask the user for guidance
- or escalate to manual review

Uncertain bypass is a doctrinal failure.

---

## Enforcement Instrument Agnosticism

The doctrine defines what enforcement must do. It does not mandate a specific enforcement instrument.

Any tool that implements the validator categories, gates, integrity protection, and proportional enforcement described above is a doctrine-compliant enforcement instrument.

The doctrine remains enforcement-instrument-agnostic — just as it is tool-agnostic, path-agnostic, identity-agnostic, and scope-agnostic.

This is the fifth agnosticism dimension: **enforcement-instrument-agnostic**.

---

## Enforcement Success Condition

The enforcement layer is functioning correctly when:
- work that is not 100% correct cannot pass as complete
- validators run at the appropriate depth for the work type
- immutable files are protected from tampering
- the 100% principle is applied proportionally
- implementation output includes the Rigid Payload
- critical rules remain active throughout the session (Prompt Salt)
- enforcement is never bypassed silently (bypasses are explicit and visible)
- the enforcement instrument is replaceable without changing the doctrine

That is the official enforcement success condition.

---

## Next File

Continue to:

`21_OPERATIONAL_STATES.md`
