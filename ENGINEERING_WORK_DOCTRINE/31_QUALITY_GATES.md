# QUALITY GATES PROTOCOL

## Purpose of This File

This file defines the official Quality Gates Protocol of the Engineering Work Doctrine.

The doctrine has readiness checks (Stage 5 — Build Readiness Verification) but does not define explicit gates at **every** stage transition. Readiness is a single checkpoint near the end of the lifecycle. It verifies that the work is ready to be built — but it does not verify that each prior stage was completed correctly before the next stage began.

Mega-tech companies do not rely on a single end-of-pipeline check. They install **quality gates at each transition** between stages: a code review gate before merge, a test gate before promotion, a security gate before release, a performance gate before scale-out. Each gate is a checkpoint that must be passed before work proceeds. If a gate fails, work stops. If a gate is bypassed, the bypass is visible, recorded, and justified.

This file defines those gates explicitly. It installs a quality gate at every stage transition in the doctrine's lifecycle, defines what each gate requires, how it is verified, when it blocks, and how it can be overridden. The result is a pipeline in which no stage begins until the prior stage has been proven complete — not assumed, not hand-waved, proven.

This file defines:
- what a quality gate is and what properties every gate must have
- the gates at each lifecycle stage transition
- the additional gates that apply to Stable state work
- how gates scale with the Operational State
- how gates can be overridden and how overrides are recorded
- how gate pass/fail is logged in the Work State File
- when the protocol has been applied successfully

---

## What Is a Quality Gate

A **quality gate** is a checkpoint that must be passed before work can proceed to the next stage. It is the boundary between two lifecycle stages. Crossing the boundary requires proof — not intention, not optimism, proof.

Every gate has four properties:

1. **Criteria** — what must be true to pass. Criteria are explicit and checkable. "The discovery is sufficient" is not a criterion unless "sufficient" is defined. Each gate's criteria are defined in this file and reference the doctrine protocols that establish them.

2. **Verification** — how the criteria are checked. Verification is one of three types:
   - **Automated** — a validator, test suite, linter, or script checks the criteria deterministically. No human judgment involved. The check passes or fails.
   - **Manual** — a human (the user or a reviewer) checks the criteria by inspection. Required when the criteria involve judgment that cannot be automated (e.g., "the user accepts the work agreement").
   - **AI self-check** — the AI evaluates the criteria against the doctrine's own standards. The AI is the executor of the doctrine, and it must verify its own work before declaring a stage complete. This is not a substitute for automated or manual verification where those apply — it is the baseline verification when no automated check exists.

3. **Blocking** — if the criteria are not met, work cannot proceed. A failed gate is not a warning. It is a stop. The work remains in the current stage until the gate passes or an override is explicitly applied. This is the core mechanism that prevents stage drift — the quiet slide from "we're still discovering" to "we're already building" without any explicit transition.

4. **Override** — under what conditions the gate can be bypassed. Gates are not absolute. The user owns the work (Rule 14.1). But an override is never silent (Rule 14.3). Every override is visible, recorded, and justified. The override conditions are defined in the Gate Override section below.

A gate without criteria is a suggestion. A gate without verification is a hope. A gate without blocking is a decoration. A gate without override is a wall. Every gate in this protocol has all four properties.

---

## Gates by Lifecycle Stage Transition

The doctrine's lifecycle has seven stages (see `03_PROJECT_LIFECYCLE.md`):

- Stage 0 — Raw Impulse
- Stage 1 — Discovery
- Stage 2 — Consolidation
- Stage 3 — Agreement
- Stage 4 — Readiness
- Stage 5 — Delivery
- Stage 6 — Evolution

A gate exists at each transition. The gate is named by the stages it connects: Gate 0→1 is the gate between Raw Impulse and Discovery.

---

### Gate 0 → 1 (Raw Impulse → Discovery)

This gate ensures that work is classified before discovery begins. Classification is the first act of the doctrine (Rule 0.1) — without it, the AI does not know which lifecycle path to follow, what process depth to apply, or what operational state governs the rules.

- **Criteria** — the work is classified. Classification has two parts:
  - **Work type** — Project, Feature, Refactoring, Bugfix, Task, or Question (see `11_TASK_CLASSIFICATION_GUIDE.md`)
  - **Operational state** — Exploratory, Formative, or Stable (see `21_OPERATIONAL_STATES.md`)
- **Verification** — AI self-check. The AI verifies that it has explicitly stated the work type and operational state before beginning discovery. If either is missing or ambiguous, the gate fails.
- **Blocking** — cannot start discovery without classification. The AI must not begin Stage 1 (Discovery) until it has explicitly classified the work. "I'll figure out the type as I go" is a gate failure.
- **Override** — see Gate Override. Classification itself (Rule 0.1) is non-negotiable and cannot be overridden — but the depth of discovery can be accelerated via Process Override (Rule 14.5).

---

### Gate 1 → 2 (Discovery → Consolidation)

This gate ensures that discovery is sufficient before consolidation begins. "Sufficient" does not mean "exhaustive" — it means that all applicable Discovery Dimension Protocol categories have been checked, and the findings are enough to consolidate into a coherent work agreement.

- **Criteria** — discovery is sufficient. Sufficiency is defined by the Discovery Dimension Protocol (`22_DISCOVERY_DIMENSION_PROTOCOL.md`): all applicable dimension categories have been checked, and for each category, either findings were recorded or the category was explicitly marked as not-applicable with justification. Discovery depth scales with work type — full discovery for Projects and Features, focused discovery for Bugfixes, quick scan for Tasks, none for Questions.
- **Verification** — AI self-check + user confirmation on key findings. The AI verifies that all applicable dimensions were checked. The user confirms the key findings — the dimensions that materially shape the work (e.g., a compliance requirement, a hardware constraint, a migration dependency). User confirmation is not required for every dimension, only for the ones that change the work's direction.
- **Blocking** — cannot consolidate if discovery dimensions are unchecked. If a applicable dimension was skipped without justification, the gate fails. The work returns to Stage 1 (Discovery) to close the gap.
- **Override** — see Gate Override. A Process Override (Rule 14.2) can skip remaining discovery dimensions, but the skipped dimensions and the risk they create must be recorded.

---

### Gate 2 → 3 (Consolidation → Agreement)

This gate ensures that consolidation is coherent before a work agreement is formed. Consolidation is the act of synthesizing discovery findings into a single, coherent understanding. If that understanding contains contradictions, hides assumptions, or leaves lacunae unclassified, the work agreement built on it will be structurally flawed.

- **Criteria** — consolidation is coherent. Coherence means:
  - no contradictions between findings (two findings that cannot both be true)
  - no hidden assumptions (every assumption is explicit and labeled as an assumption, not presented as a fact)
  - lacunae are classified (every gap in understanding is identified as a lacuna and classified as blocking or non-blocking — see `05_CONSOLIDATION_PROTOCOL.md`)
- **Verification** — AI self-check. The AI reviews the consolidated understanding for contradictions, hidden assumptions, and unclassified lacunae. This is a structural coherence check, not a content check — the AI is not verifying that the findings are correct, only that they are internally consistent and explicitly stated.
- **Blocking** — cannot form agreement if consolidation is incoherent. If contradictions exist, they must be resolved. If assumptions are hidden, they must be surfaced. If lacunae are unclassified, they must be classified. The work returns to Stage 2 (Consolidation) until coherence is achieved.
- **Override** — see Gate Override. A Process Override can proceed with known contradictions or unclassified lacunae, but each must be recorded with the risk it creates.

---

### Gate 3 → 4 (Agreement → Readiness)

This gate ensures that the work agreement is accepted by the user before readiness verification begins. The work agreement is the contract between the user and the AI — it defines what will be built, why, and with what scope. If the user has not accepted it, readiness verification is premature: the AI would be verifying readiness for work the user has not agreed to.

- **Criteria** — the work agreement is accepted by the user. Acceptance is explicit — the user must confirm that the work agreement reflects their intent. Silence is not acceptance. "I guess" is not acceptance. The user must actively confirm.
- **Verification** — explicit user acceptance. This is a manual gate. The AI presents the work agreement and asks the user to confirm. No automated check can substitute for user judgment here.
- **Blocking** — cannot proceed to readiness without user acceptance. If the user has not accepted, the work remains in Stage 3 (Agreement). The AI may revise the agreement based on user feedback, but it must not advance to Stage 4 (Readiness) until acceptance is explicit.
- **Override** — this gate cannot be overridden by Process Override. User acceptance is not a process step that can be skipped — it is the consent that authorizes the work. The user can always revise the agreement, but they cannot "skip" accepting it. (A user who says "just proceed" has accepted — the acceptance is implicit in the instruction to proceed, and the AI records it as such.)

---

### Gate 4 → 5 (Readiness → Delivery)

This gate ensures that readiness is explicit before delivery begins. Readiness is not a feeling — it is an explicit judgment (Rule 7.1) that the work's core identity is stable (Rule 7.2) and that no critical blocking lacunae remain.

- **Criteria** — readiness is explicit. This means:
  - the AI has explicitly declared the work ready (Rule 7.1 — readiness must be stated, not assumed)
  - core identity is stable (Rule 7.2 — the fundamental decisions that define the work are settled, not still in flux)
  - no critical blocking lacunae remain (every blocking lacuna has been resolved or explicitly deferred with justification)
- **Verification** — AI readiness judgment. The AI must make an explicit readiness judgment — not "I think we're ready" but a structured statement that the readiness criteria are met, referencing the specific evidence. The judgment must be explicit because implicit readiness is no readiness at all (Rule 7.1).
- **Blocking** — cannot begin delivery without explicit readiness. If the AI cannot make an explicit readiness judgment, the work is not ready. It returns to Stage 4 (Readiness) to close the gaps. "We'll figure it out during delivery" is a gate failure.
- **Override** — see Gate Override. A Process Override can proceed to delivery without full readiness, but the unmet readiness criteria and the risk they create must be recorded. A Quality Override is not appropriate here — readiness is a process gate, not a quality standard.

---

### Gate 5 → 6 (Delivery → Evolution)

This gate ensures that delivery is complete before the work transitions to evolution. "Complete" means 100% — not 95%, not "mostly done," not "done except for the parts we'll handle later." The 100% criterion is the floor (Operational Principle 2), and its definition varies by operational state.

- **Criteria** — all of the following are met:
  - **100% criterion met** — per the operational state's definition of 100% (see `21_OPERATIONAL_STATES.md`). In Stable state, this is the full standard. In Formative state, this is the committed scope. In Exploratory state, this is the exploration goal.
  - **Rigid Payload complete** — per the operational state's requirements (see `07_DELIVERY_PROTOCOL.md`). The Rigid Payload captures what was built, what changed, and how it was verified.
  - **Tests pass** — per the Testing Strategy Protocol (`23_TESTING_STRATEGY_PROTOCOL.md`). All required test types for the work type and operational state pass.
  - **Security reviewed** — per the Security Review Protocol (`26_SECURITY_REVIEW_PROTOCOL.md`). Security review is completed for Stable state work.
  - **Observability added** — per the Observability Protocol (`25_OBSERVABILITY_PROTOCOL.md`). Observability is present for Stable state work.
- **Verification** — automated validators + AI self-check. Automated validators run the test suite, linters, and security scans. The AI self-check verifies that the Rigid Payload is complete, that observability is present, and that all protocol requirements are met. Where automated checks exist, they are authoritative. Where they do not, the AI self-check is the baseline.
- **Blocking** — cannot declare complete without passing all applicable gates. If any criterion fails, the work is not complete. It remains in Stage 5 (Delivery) until all criteria pass or overrides are applied. Declaring incomplete work complete is a doctrinal failure.
- **Override** — see Gate Override. A Quality Override (Rule 14.2) can accept less than 100%, but the work must be labeled "user-accepted incomplete," not "done," and the quality gap must be recorded.

---

## Additional Gates for Stable State

The lifecycle gates above govern stage transitions. In Stable state, additional gates govern the quality of the work itself — the checks that mega-tech companies install in their delivery pipelines. These gates apply to Stable state work and are mandatory and blocking. In Formative state, they apply when committing. In Exploratory state, they are advisory.

### Code Review Gate

- **Criteria** — code is reviewed by a human or AI before merge. Review checks for correctness, clarity, adherence to project conventions, and absence of obvious defects. Review is not a rubber stamp — it is a substantive check.
- **Verification** — manual (human reviewer) or AI self-check (AI reviewer). In AI-driven work, the AI reviews its own output against the doctrine's quality standards (`09_OUTPUT_QUALITY_STANDARD.md`) before declaring the code reviewed.
- **Blocking** — code cannot merge without review in Stable state.
- **Override** — Process Override can skip review with risk recorded.

### Test Gate

- **Criteria** — all required test types pass, per the Testing Strategy Protocol (`23_TESTING_STRATEGY_PROTOCOL.md`). The required types depend on work type and operational state. In Stable state, this typically includes unit, integration, and where applicable, end-to-end tests.
- **Verification** — automated. The test suite runs and passes. No human judgment involved.
- **Blocking** — code cannot merge or be declared complete with failing tests in Stable state.
- **Override** — Quality Override can accept failing tests, but the work is labeled "user-accepted incomplete" and the failing tests are recorded as quality gaps.

### Security Gate

- **Criteria** — security review is completed, per the Security Review Protocol (`26_SECURITY_REVIEW_PROTOCOL.md`). For Stable state, this includes the applicable security checks (input validation, authentication, authorization, secrets, dependencies, data protection).
- **Verification** — automated scans + AI self-check. Automated tools scan for known vulnerabilities. The AI self-check verifies that the security review was conducted and findings addressed or recorded.
- **Blocking** — code cannot be declared complete in Stable state without security review.
- **Override** — Quality Override can accept unaddressed security findings, but the work is labeled "user-accepted incomplete" and the findings are recorded as quality gaps. Security overrides in Stable state carry high risk and must be explicitly justified.

### Performance Gate

- **Criteria** — performance tests pass if NFRs apply. NFRs (non-functional requirements) are identified during discovery (Discovery Dimension Protocol Category 3 — see `22_DISCOVERY_DIMENSION_PROTOCOL.md`). If the work has performance NFRs (latency, throughput, resource usage), performance tests must pass against the defined thresholds.
- **Verification** — automated (performance test suite) or AI self-check (if no automated performance tests exist, the AI verifies that the work meets the NFR thresholds by analysis).
- **Blocking** — code cannot be declared complete in Stable state if performance NFRs are not met.
- **Override** — Quality Override can accept unmet NFRs, but the work is labeled "user-accepted incomplete" and the unmet NFRs are recorded as quality gaps.

### Documentation Gate

- **Criteria** — documentation is updated, per the Documentation Protocol (`29_DOCUMENTATION_PROTOCOL.md`). For Stable state, this means all documentation types required by the work type are created or updated, and the Rigid Payload's Alterações section lists what documentation changed.
- **Verification** — AI self-check. The AI verifies that documentation exists, is accurate, and is listed in the Rigid Payload.
- **Blocking** — code cannot be declared complete in Stable state without documentation updates.
- **Override** — Process Override can defer documentation, but the deferral is recorded as documentation debt (see `29_DOCUMENTATION_PROTOCOL.md`).

### Deployment Gate

- **Criteria** — deployment strategy is defined and rollback plan is verified, per the Enforcement Layer (`20_ENFORCEMENT_LAYER.md`). For Stable state work that is deployed, the work must include a defined deployment strategy and a verified rollback plan. A system that can be deployed but cannot be rolled back is not production-ready.
- **Verification** — AI self-check. The AI verifies that the deployment strategy is stated and the rollback plan is defined and verified (not just written — verified, meaning it has been tested or validated against the system's actual structure).
- **Blocking** — work cannot be declared complete in Stable state without a deployment and rollback plan.
- **Override** — Process Override can defer the deployment and rollback plan, but the deferral is recorded with the risk it creates (inability to safely deploy or roll back).

### ADR Gate

- **Criteria** — all significant architectural decisions have recorded ADRs, per the ADR Protocol (`24_ARCHITECTURE_DECISION_RECORDS.md`). For Stable state, any decision that affects the system's structure, external interfaces, data model, or technology choices must have an ADR. Trivial implementation choices do not require ADRs.
- **Verification** — AI self-check. The AI verifies that ADRs exist for all significant decisions made during the work.
- **Blocking** — work cannot be declared complete in Stable state without ADRs for significant decisions.
- **Override** — Process Override can defer ADR creation, but the deferral is recorded as documentation debt.

### Technical Debt Gate

- **Criteria** — all intentional debt is tracked in the Debt Register, per the Technical Debt Protocol (`27_TECHNICAL_DEBT_PROTOCOL.md`). For Stable state, no untracked debt may survive into completion. Every debt item must have a type, severity, reason, and payoff plan.
- **Verification** — AI self-check. The AI verifies that the Debt Register is updated and no untracked debt exists.
- **Blocking** — work cannot be declared complete in Stable state with untracked debt.
- **Override** — Quality Override can accept untracked debt, but the work is labeled "user-accepted incomplete" and the debt is recorded as a quality gap.

### Dependency Gate

- **Criteria** — all dependencies are evaluated, pinned to exact versions, and security-scanned, per the Dependency Management Protocol (`28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`). For Stable state, lockfiles are committed, no vulnerable dependencies are present (or vulnerabilities are explicitly accepted), and every new dependency has an evaluation record.
- **Verification** — automated (dependency scan) + AI self-check. Automated tools scan for known vulnerabilities. The AI self-check verifies that dependencies are pinned and evaluated.
- **Blocking** — code cannot be declared complete in Stable state with unevaluated or vulnerable dependencies.
- **Override** — Quality Override can accept vulnerable dependencies, but the work is labeled "user-accepted incomplete" and the vulnerabilities are recorded as quality gaps.

### Data Governance Gate

- **Criteria** — all data touched by the work is classified, access control is verified, retention policy is defined, and encryption is confirmed for Confidential/Restricted data, per the Data Governance Protocol (`33_DATA_GOVERNANCE_PROTOCOL.md`). For Stable state, no unclassified data may survive into completion.
- **Verification** — AI self-check. The AI verifies that data classification is complete and handling rules are followed.
- **Blocking** — work cannot be declared complete in Stable state with unclassified data or unverified access control.
- **Override** — Quality Override can accept data governance gaps, but the work is labeled "user-accepted incomplete" and the gaps are recorded as quality gaps. Data governance overrides in Stable state carry high risk and must be explicitly justified.

### Observability Gate

- **Criteria** — logs, metrics, traces, alerts, and dashboards are present for the stabilized surface area, per the Observability Protocol (`25_OBSERVABILITY_PROTOCOL.md`). For Stable state, the work must be observable — runtime behavior must be understandable without debugging in production.
- **Verification** — AI self-check. The AI verifies that required observability infrastructure is in place and that the work's runtime behavior is captured.
- **Blocking** — work cannot be declared complete in Stable state without required observability infrastructure.
- **Override** — Quality Override can accept observability gaps, but the work is labeled "user-accepted incomplete" and the gaps are recorded as quality gaps.

### API Governance Gate

- **Criteria** — if the work touches API surfaces, API changes are reviewed for naming, versioning, error handling, and breaking change management, per the API Governance Protocol (`32_API_GOVERNANCE_PROTOCOL.md`). For Stable state, breaking changes require version bumps and migration guides.
- **Verification** — AI self-check. The AI verifies that API changes follow governance rules and that breaking changes are properly versioned.
- **Blocking** — work cannot be declared complete in Stable state with unreviewed API changes or unversioned breaking changes.
- **Override** — Quality Override can accept API governance gaps, but the work is labeled "user-accepted incomplete" and the gaps are recorded as quality gaps.

### Incident Response Gate

- **Criteria** — if the work is deployed to production, the rollback plan is verified and the incident response procedure is documented, per the Incident Response Protocol (`30_INCIDENT_RESPONSE_PROTOCOL.md`). For Stable state, the work must be rollback-ready and the team must know how to respond to incidents.
- **Verification** — AI self-check. The AI verifies that a rollback plan exists and that incident response procedures are documented.
- **Blocking** — work cannot be declared complete in Stable state without a verified rollback plan (if deployed) or documented incident response.
- **Override** — Quality Override can accept incident response gaps, but the work is labeled "user-accepted incomplete" and the gaps are recorded as quality gaps.

### Metrics Gate

- **Criteria** — success metrics are defined and collection mechanisms are in place, per the Metrics & Feedback Loop Protocol (`34_METRICS_FEEDBACK_LOOP.md`). For Stable state, DORA metrics (deployment frequency, lead time, change failure rate, MTTR) and doctrine compliance metrics must be collectable.
- **Verification** — AI self-check. The AI verifies that metrics are defined and that collection mechanisms are in place.
- **Blocking** — work cannot be declared complete in Stable state without defined success metrics and collection mechanisms.
- **Override** — Quality Override can accept metrics gaps, but the work is labeled "user-accepted incomplete" and the gaps are recorded as quality gaps.

---

## Gates by Operational State

Gates scale with the Operational State, like all doctrine protocols. The preciousness and reversibility of the output determine how strict the gates are.

### Exploratory State

- **Gate 0→1 only (classification) is mandatory and blocking.** Classification is non-negotiable (Rule 0.1). Even exploratory work must be classified — the AI must know it is exploring, not building.
- **All other gates are advisory.** The AI notes them but does not block. Exploratory work is throwaway by definition — installing blocking gates on a prototype that may be discarded is ceremony that kills exploration.
- Advisory gates are still logged (see Gate Logging). The log records that the gate was advisory and was not enforced.

### Formative State

- **Gates 0→1, 1→2, and 2→3 are mandatory and blocking.** Classification, discovery sufficiency, and consolidation coherence are required — the work is taking shape, and these gates ensure the shape is sound.
- **Gates 4→5 and 5→6 apply when committing.** During active development, the AI may iterate without enforcing every gate. But when the work is committed — merged, pushed, deployed — the readiness and completion gates apply. The bar is "gates pass for committed work," not "gates pass for every intermediate state."
- The additional Stable state gates (code review, test, security, performance, documentation, deployment, ADR, technical debt, dependency, data governance, observability, API governance, incident response, metrics) apply when committing, at the level appropriate to the work's maturity.

### Stable State

- **All gates are mandatory and blocking.** Every stage transition gate, every additional gate — all are enforced. Stable work is production-grade. No gate is advisory. No gate is skipped without an explicit override.
- This is the full quality pipeline. It is the standard that mega-tech companies apply to production systems, and it is the standard the doctrine applies to Stable work.

This scaling prevents two failure modes:
1. **Requiring all gates in Exploratory** — kills exploration with ceremony
2. **Not requiring gates in Stable** — leaves production work without quality protection when it matters most

---

## Gate Override

Gates can be overridden — but only through the User Override Protocol (Rule Set 14, see `08_DECISION_RULES.md`). The user owns the work (Rule 14.1). But an override is never silent (Rule 14.3).

There are two types of override, matching the doctrine's existing distinction (Rule 14.2):

### Process Override

A **Process Override** is applied when the user wants to skip or accelerate a gate — i.e., the gate's process is skipped, not the gate's quality standard. For example: "skip the discovery dimensions, I know what I want."

When a Process Override is applied to a gate:
- the gate is noted as **skipped** in the Work State File
- the risk of skipping is stated (what could go wrong because the gate was not enforced)
- the work proceeds with the override noted

Process Overrides are appropriate for gates that verify process completeness (Gate 0→1 classification is non-negotiable and cannot be overridden; Gate 1→2 discovery sufficiency can be overridden; Gate 2→3 consolidation coherence can be overridden; Gate 4→5 readiness can be overridden).

### Quality Override

A **Quality Override** is applied when the user wants to accept work that does not meet a gate's quality standard — i.e., the gate was checked and failed, and the user accepts the failure. For example: "ship it even though the security scan has findings."

When a Quality Override is applied to a gate:
- the gate is noted as **not-met** in the Work State File
- the quality gap is recorded (what specifically did not pass)
- the work is labeled "user-accepted incomplete" where the 100% criterion is concerned
- the Rigid Payload's Enforcement section records the override, not a pass

Quality Overrides are appropriate for gates that verify quality standards (Test Gate, Security Gate, Performance Gate, Gate 5→6 completion).

### Override Is Never Silent

Regardless of type, every gate override must be:
1. **acknowledged explicitly** — the AI states that a gate is being overridden
2. **recorded** — the override is logged in the Work State File (see Gate Logging)
3. **justified** — the reason for the override and the risk it creates are stated
4. **visible** — the override appears in the work's output, not buried in a log

Silent compliance with an override is a doctrinal failure (Rule 14.3). The AI must not pretend a gate passed when it was overridden.

---

## Gate Logging

Gate pass/fail must be recorded in the Work State File (see `13_PROJECT_SESSION_TEMPLATE.md`). The Work State File is the persistent memory of the work's doctrinal position — and gate status is part of that position.

For every gate check, the Work State File records:

1. **Which gate** — the gate identifier (e.g., "Gate 1→2", "Test Gate", "Security Gate")
2. **When it was checked** — timestamp or session reference
3. **Pass/fail status** — the gate passed, failed, or was advisory (in Exploratory state)
4. **Override (if any) with justification** — if the gate was overridden, the override type (Process or Quality), the reason, and the risk

This log is the audit trail of the work's quality journey. It allows any subsequent session — or any reviewer — to see which gates were enforced, which passed, which failed, and which were overridden. A work item with no gate log has no evidence that its quality was verified. A work item with a gate log that shows overrides has visible, justified deviations — not hidden gaps.

---

## Quality Gate Anti-Patterns

The following are quality gate anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Gate as suggestion** — a gate that is documented but not enforced. The team knows the gate exists, but it can be bypassed without recording or justification. A gate that is not enforced is not a gate.
- **Gate that doesn't verify** — a gate that checks for the presence of an artifact but not its quality. "Tests exist" is not "tests pass." "Documentation exists" is not "documentation is accurate."
- **No gate for critical transitions** — a stage transition that occurs without a gate. Work moves from discovery to delivery without verifying that discovery was sufficient.
- **Override without recording** — a gate is overridden, but the override is not documented. The team doesn't know the gate was bypassed, doesn't know why, and doesn't know the risk.
- **Gate that doesn't scale with state** — the same gate strictness applied to Exploratory and Stable work. Exploratory work is killed by ceremony; Stable work is endangered by laxness.
- **No gate logging** — gates run, but the results are not recorded. There is no audit trail of what passed, what failed, and what was overridden.

---

## Quality Gates and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that all applicable quality gates pass (test gate, security gate, documentation gate, deployment gate, ADR gate, debt gate, dependency gate, data governance gate, observability gate, API gate, incident gate, metrics gate). No work enters Stable state with failing gates.

---

## Protocol Success Condition

The Quality Gates Protocol has been applied successfully when:

1. Every stage transition in Stable state has passed its gate — no transition occurred without the prior gate being verified.
2. Every additional Stable state gate (code review, test, security, performance, documentation, deployment, ADR, technical debt, dependency, data governance, observability, API governance, incident response, metrics) has passed for the completed work.
3. Any gate override is explicitly documented with the override type, the reason, and the risk it creates — no override is silent.
4. Every gate check is recorded in the Work State File with the gate identifier, timestamp, pass/fail status, and override details if applicable.
5. The strictness of gate enforcement matches the Operational State — mandatory and blocking in Stable, applied when committing in Formative, advisory (except classification) in Exploratory.

That is the official success condition of the Quality Gates Protocol.

**Anti-pattern:** See ANTI-PATTERN 39 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.10 in `08_DECISION_RULES.md`.

---

## Next File

Continue to:

`32_API_GOVERNANCE_PROTOCOL.md`
