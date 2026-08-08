# BUILD READINESS CHECKLIST

## Purpose of This File

This file defines the official build readiness gate of the Engineering Work Doctrine.

Its purpose is to determine whether work may responsibly enter serious structured delivery.

> **Proportionality Note:** Readiness verification depth scales with work type. Full build readiness (described here) applies to projects. For features, implementation readiness is sufficient. For refactoring, change readiness. For bugfixes, fix readiness. For tasks, a lightweight check. For questions, no readiness gate is needed. See the relevant lifecycle path in `03_PROJECT_LIFECYCLE.md`.

> **Operational State Note:** Readiness depth also scales with Operational State. In Stable state, the full readiness gate applies. In Formative state, a lighter check is sufficient (the work is still being shaped). In Exploratory state, no readiness gate is needed (the output is throwaway). See `21_OPERATIONAL_STATES.md` for state definitions.

The doctrine rejects the idea that work is ready to build because:
- it sounds exciting
- the user is impatient
- several messages have already been exchanged
- some architecture has already been imagined
- the conversation feels advanced
- the AI is tempted to “keep momentum”

Readiness must not be assumed.  
Readiness must be judged.

This file exists to create that judgment.

---

## Role of Build Readiness in the Doctrine

Build readiness sits between:
- consolidation
- and structured delivery

Its role is to answer one decisive question:

**Can serious construction-relevant delivery begin now without irresponsible guesswork?**

This is not a ceremonial step.

It is the formal gate that protects the work from:
- premature implementation
- hidden blockers
- architecture built on false certainty
- scope drift disguised as progress
- rework caused by incomplete work initiation
- structural fragility caused by conversational enthusiasm

Without a build readiness gate, the doctrine loses one of its most important protections.

---

## Build Readiness Principle

A project is build-ready only when its structural clarity is sufficient to support serious delivery without relying on hidden assumptions for core work identity.

This does not mean every detail must already be known.

It means that:
- the work must be coherent enough
- the major dimensions must be visible enough
- the unresolved items must be governed enough
- the structural direction must be real enough

for serious delivery to begin responsibly.

The doctrine does not require impossible completeness.  
It requires explicit legitimacy.

---

## What Build Readiness Is Not

Build readiness is not:

- emotional readiness
- motivational readiness
- conversational momentum
- architectural curiosity
- user urgency alone
- “good enough because we can always fix later”
- excitement about possibilities
- the AI wanting to impress with output volume

None of these are valid criteria.

A project may be exciting and still not be ready.  
A project may be ambitious and still not be ready.  
A project may be partially clarified and still not be ready.

Readiness must be earned through doctrine-compliant maturity.

---

## Official Readiness Question

The official readiness question is:

**Has this work been sufficiently discovered, sufficiently consolidated, and sufficiently bounded that serious structured delivery may begin without violating doctrinal integrity?**

If the answer is no, delivery must not begin yet.

If the answer is partially, the specific blockers or reservations must be made explicit.

If the answer is yes, the work may proceed into structured delivery.

---

## Readiness Evaluation Categories

Readiness must be evaluated across the following categories.

### 1. Work Identity Clarity
Is the work clearly defined as a specific kind of thing?

### 2. Purpose Clarity
Is it clear what the work exists to accomplish?

### 3. Actor Clarity
Is it sufficiently clear who uses, operates, administers, or depends on the work?

### 4. Operational Flow Clarity
Are the main flows or core operational dynamics understood well enough?

### 5. Data and Record Clarity
Is it clear enough what must be stored, tracked, auditable, or protected?

### 6. Control and Governance Clarity
Are permissions, restrictions, approvals, histories, or accountability layers understood well enough?

### 7. Scope Boundary Clarity
Is the distinction between present confirmed scope and plausible future horizon sufficiently clear?

### 8. Lacuna Governance
Are the remaining unknowns visible and properly classified?

### 9. Structural Implication Clarity
Are the main architectural or systemic consequences already visible enough?

### 10. Constraint Clarity
Are the real constraints known well enough to prevent irresponsible delivery?

### 11. Agreement Integrity
Does a coherent Work Agreement candidate exist?

### 12. Delivery Legitimacy
Can delivery now begin without pretending certainty where there is still unacceptable uncertainty?

These are the minimum readiness dimensions.

---

## Build Readiness Checklist

The AI must evaluate the following questions explicitly.

### A. Identity and Purpose

- Is it clear what the work fundamentally is?
- Is it clear what the work is not?
- Is it clear what the work exists to make possible?
- Is it clear enough what success would mean for this work?

### B. Users and Actors

- Are the principal actors identified?
- Is it sufficiently clear who uses, operates, administers, controls, or depends on the work?
- If permissions matter, is the actor model clear enough to begin?

### C. Operational Logic

- Are the main flows or operational loops known well enough?
- Is it clear enough what the work must support in practice?
- Are the most important events, actions, or transitions visible enough?

### D. Data and Memory

- Is it clear enough what information must be stored?
- Is it clear enough what must be visible, retrievable, or auditable?
- Is it clear enough where state, history, or traceability matter?

### E. Control and Governance

- Are the most important control layers understood?
- Is it clear enough what needs permissions, restrictions, approvals, or logs?
- If the work is governance-sensitive, are those sensitivities sufficiently visible?

### F. Scope and Horizon

- Is confirmed present scope distinguishable from future possibilities?
- Is the work protected from either shallow reduction or inflated overdesign?
- Is the structural foundation needed at initiation visible enough?

### G. Unknowns and Lacunae

- Have the important unknowns been surfaced?
- Have they been classified as critical blocking, important non-blocking, or evolutive?
- Are there any unresolved unknowns that would make serious delivery irresponsible?

### H. Constraints and Environment

- Are the important constraints known?
- Are device, connectivity, environment, ownership, deployment, or skill realities known where relevant?
- Would beginning delivery now violate a known real-world constraint?

### I. Agreement Readiness

- Can the work already be expressed coherently as a Work Agreement?
- Is the work agreement candidate stable enough to support build-oriented work?
- Is the work no longer merely clarified, but formally interpretable?

### J. Delivery Legitimacy

- Can serious delivery begin without concealed assumptions in the work's core identity?
- Can architecture, structure, data, and implementation logic now be discussed responsibly?
- Would beginning delivery now preserve doctrinal integrity?

---

## Readiness Decision Outcomes

The build readiness gate may result in one of the following outcomes.

### Outcome 1 — Ready for Structured Delivery
The work has sufficient doctrinal maturity to begin serious structured delivery.

This means:
- identity is coherent
- contract logic is real
- critical blockers are absent or resolved
- major dimensions are visible enough
- remaining uncertainty is governed

Delivery may begin.

---

### Outcome 2 — Not Ready Due to Critical Blocking Lacunae
The work cannot yet responsibly enter structured delivery.

This means:
- one or more critical unknowns remain unresolved
- delivery would rely on irresponsible guesswork
- further discovery and/or consolidation is required

Delivery must not begin.

The AI must state clearly:
- what blocks readiness
- why it blocks readiness
- what must be clarified or resolved

---

### Outcome 3 — Conditionally Ready with Explicit Reservations
The work is sufficiently mature to begin delivery, but only if specific reservations are made explicit.

This means:
- no critical blockers remain
- some important non-blocking lacunae remain open
- those lacunae are visible and governable
- delivery can proceed if it does not pretend those lacunae are resolved

Delivery may begin with explicit reservation handling.

---

### Outcome 4 — Return Required to Earlier Stage
The work has not yet reached legitimate readiness because the issue is not merely a missing detail, but a lifecycle problem.

This may happen when:
- discovery was too shallow
- consolidation is fragmented
- work identity is still unstable
- scope and horizon are mixed
- an agreement candidate does not yet exist coherently

In this case, the AI must identify whether the work must return to:
- discovery
- consolidation
- contract refinement
- agreement refinement

Delivery must not begin until the lifecycle breach is corrected.

---

## Minimum Conditions for a "Ready" Decision

A project must not be marked as ready unless all of the following are true:

1. the work has a coherent identity
2. its purpose is clear enough
3. its main actors are sufficiently understood
4. its main operational logic is sufficiently visible
5. its core data/control implications are visible enough
6. the distinction between confirmed scope and plausible horizon is explicit
7. critical blocking lacunae are absent or resolved
8. remaining important unknowns are visible and classified
9. a coherent Work Agreement candidate exists
10. delivery can begin without hidden assumptions corrupting core identity

**For Stable state work**, readiness also requires awareness of the mega-tech protocol requirements (files 23-34). The work agreement must identify which protocols apply and at what level. See `12_TEMPLATE_WORK_AGREEMENT.md` Section 21.7 for the mega-tech protocol requirements field.

If any of these fail materially, readiness should not be granted.

---

## How the AI Must Explain a Readiness Decision

The AI must not merely declare readiness.

It must explain the decision in structurally meaningful terms.

A doctrine-compliant readiness decision should include:

### 1. Readiness Status
One of:
- Ready
- Not Ready
- Conditionally Ready
- Return Required

### 2. Reasoning Summary
Why that status was reached.

### 3. Strengths Already Present
What is sufficiently mature already.

### 4. Remaining Unknowns
What remains open.

### 5. Blocking Factors, If Any
What specifically prevents readiness.

### 6. Required Next Step
What should happen next in the lifecycle.

This makes readiness auditable rather than theatrical.

---

## Readiness and Partial Knowledge

The doctrine does not require total specification before readiness.

Readiness may still be valid when:
- some future details remain open
- some secondary flows remain underdefined
- some optimization choices are not yet fixed
- some evolutive decisions remain later-bound

However, readiness is invalid when unknowns affect:
- core identity
- actor model
- major operational logic
- decisive structural class
- essential environment assumptions
- major governance or data implications

The AI must distinguish partial knowledge from unacceptable uncertainty.

---

## Readiness Failure Modes

Build readiness evaluation has failed when:

- readiness is granted because the conversation “feels mature”
- readiness is denied because the AI demands impossible completeness
- hidden assumptions are ignored
- major blockers are treated as minor
- important non-blocking lacunae are mislabeled as critical
- lifecycle confusion is mistaken for a simple missing detail
- the project contract is unstable but still treated as sufficient
- the work agreement is unstable but still treated as sufficient
- the AI uses readiness to justify premature architecture
- readiness language sounds strong but lacks doctrinal logic

These are doctrinal readiness failures.

---

## Readiness Success Condition

Build readiness evaluation is successful when:

- the decision is explicit
- the status is structurally justified
- the major strengths and gaps are visible
- critical blockers are governed correctly
- uncertainty is not hidden
- delivery is allowed only when legitimate
- the next lifecycle step is clear

That is the official success condition of the readiness gate.

---

## Readiness Summary Template

A doctrine-compliant readiness summary may be structured like this:

### Build Readiness Status
[Ready / Not Ready / Conditionally Ready / Return Required]

### Why
[Short structural explanation]

### What Is Already Mature Enough
- [...]
- [...]
- [...]

### What Remains Open
- [...]
- [...]
- [...]

### Blocking Issues
- [...]
- [...]
- [...]

### Correct Next Step
[Discovery / Consolidation / Contract refinement / Structured delivery]

This template is not the only valid form, but it captures the doctrinal logic.

---

## Final Rule

No serious structured delivery may begin unless the work has passed the readiness gate explicitly.

This rule is mandatory.

If delivery begins without explicit readiness, the doctrine has been violated.

---

## Next File

Continue to:

`07_DELIVERY_PROTOCOL.md`