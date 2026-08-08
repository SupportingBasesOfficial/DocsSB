# VERSIONING POLICY

> **Doctrine version:** 0.8.1

## Purpose of This File

This file defines the official versioning policy of the Engineering Work Doctrine.

Its purpose is to ensure that the doctrine evolves in a governed, interpretable, and traceable way over time.

A doctrine that changes without version discipline becomes:
- unstable
- semantically inconsistent
- hard to audit
- hard to trust
- difficult to reuse
- vulnerable to silent degradation

This file exists to prevent that.

The doctrine must evolve, but it must evolve with memory, structure, and visible consequence.

---

## Role of Versioning in the Doctrine

Versioning is not cosmetic labeling.

Within this doctrine, versioning serves to:

- preserve historical traceability
- stabilize meaning over time
- make revisions interpretable
- distinguish small edits from structural changes
- protect cross-file coherence
- support doctrine governance
- allow future refinement without silent drift

Without versioning, the doctrine may still grow, but it cannot grow responsibly.

---

## Versioning Principle

Every meaningful change to the doctrine must be classifiable by impact.

The doctrine must not treat all changes as equal.

Some changes are:
- minor corrections
- structural clarifications
- new operational rules
- semantic redefinitions
- lifecycle changes
- instrument additions
- governance refinements

These changes affect doctrine stability differently.

Versioning exists to preserve that difference.

---

## Official Versioning Model

The Engineering Work Doctrine uses a three-level versioning model:

`MAJOR.MINOR.PATCH`

Example:
`1.0.0`

Each level has a different meaning.

---

## MAJOR Version Changes

A **MAJOR** version change occurs when the doctrine changes in a way that materially alters its identity, logic, lifecycle, or interpretive foundation.

Examples of MAJOR changes:

- changing the doctrinal lifecycle itself
- redefining the core role of the AI
- changing the formal meaning of project birth
- altering the doctrine's truth-status model
- altering readiness logic in a way that changes the behavior of the system
- changing the doctrine's fundamental structure or constitutional principles
- introducing a new governing paradigm that makes prior usage materially non-equivalent

### MAJOR Version Rule
Increment MAJOR when prior doctrine interpretation would no longer remain meaningfully compatible without explicit adjustment.

Examples:
- `1.4.7` → `2.0.0`

---

## MINOR Version Changes

A **MINOR** version change occurs when the doctrine grows or becomes operationally stronger without changing its core identity.

Examples of MINOR changes:

- adding a new doctrinal file that extends the framework
- adding new anti-patterns
- adding new decision rules that clarify behavior without changing foundational logic
- refining an existing protocol significantly
- improving template structure in a way that adds capability
- extending glossary coverage
- improving governance mechanisms
- adding a new official usage path

### MINOR Version Rule
Increment MINOR when the doctrine becomes meaningfully more capable, complete, or robust, but remains interpretively compatible with prior major identity.

Examples:
- `1.2.3` → `1.3.0`

---

## PATCH Version Changes

A **PATCH** version change occurs when the doctrine is corrected, clarified, cleaned up, or improved in ways that do not materially change its operational meaning.

Examples of PATCH changes:

- typo fixes
- wording cleanup
- formatting corrections
- minor clarification that does not alter logic
- better phrasing of an already existing rule
- correction of internal references
- small improvements to examples or readability

### PATCH Version Rule
Increment PATCH when the doctrine becomes cleaner or more precise without altering doctrine behavior in a meaningful way.

Examples:
- `1.2.3` → `1.2.4`

---

## Initial Versioning Recommendation

The doctrine should begin in an explicit pre-stable phase.

Recommended progression:

### Early Formation Phase
Use:
- `0.1.0`
- `0.2.0`
- `0.3.0`
- etc.

This indicates:
- the doctrine already exists
- it is operational
- but it is still being formed through real use and refinement

### First Stable Release
Use:
- `1.0.0`

This should be declared only when:
- the doctrine's core logic is stable
- the lifecycle is stable
- the key files are complete enough
- the doctrine has been used in real sessions
- major semantic instability is no longer expected

This policy strongly recommends **not** jumping straight to `1.0.0` without practical validation.

---

## Version Meaning Rule

A version number must communicate the maturity and stability meaningfully.

This means:

- `0.x.x` = operational but still in formation
- `1.x.x` = stable doctrine line
- `2.x.x` and beyond = materially revised doctrine generations

Version numbers must not be assigned casually.

They must reflect real doctrinal state.

---

## File-Level vs Doctrine-Level Changes

Not every file change automatically changes the doctrine version at the same level of significance.

The correct rule is:

### File-Level Change
A change to one document may be:
- local
- structural
- semantic
- doctrinally consequential

### Doctrine-Level Version
The doctrine version must reflect the **total impact** of the change on the framework as a whole.

This means:
- a major change in one file may trigger a doctrine MAJOR change
- a small wording update in many files may still only be PATCH
- a new file may trigger MINOR if it expands capability without redefining the doctrine

Versioning must be impact-based, not merely count-based.

### Mega-tech Protocol Versioning
The 12 mega-tech protocols (files 23-34) are versioned as part of the doctrine. Adding a new protocol is a MINOR change (expands capability). Changing a protocol's requirements (e.g., adding a new test type, changing a security review level threshold) is a MINOR change if it affects existing work, or a PATCH if it only clarifies. Removing a protocol is a MAJOR change. Each protocol change must be logged in `18_EVOLUTION_LOG.md` with the protocol file name and what changed.

---

## Official Change Classification Process

Before changing the doctrine version, evaluate the change using this sequence:

### Step 1 — What Changed?
Describe the actual change.

### Step 2 — What Layer Was Affected?
Examples:
- foundation
- lifecycle
- protocol
- instrument
- governance
- vocabulary
- quality standard

### Step 3 — What Is the Operational Impact?
Did it:
- change how the doctrine behaves?
- change how the doctrine is interpreted?
- add a new capability?
- clarify existing behavior only?

### Step 4 — What Version Level Matches That Impact?
Choose:
- MAJOR
- MINOR
- PATCH

### Step 5 — Log the Change Explicitly
Record it in:
- `18_EVOLUTION_LOG.md`

This process is mandatory for meaningful version changes.

---

## Versioning and Backward Interpretation

When a version changes, the doctrine should preserve interpretability of earlier versions whenever possible.

This means:
- do not silently rewrite history
- do not pretend older doctrine versions meant what newer ones mean
- preserve awareness of what changed and why
- keep the evolution legible

If an old project was born under an earlier doctrine version, that context may matter.

Versioning preserves that context.

---

## Compatibility Guidance

### PATCH Compatibility
PATCH changes should be considered fully compatible.

### MINOR Compatibility
MINOR changes should generally be compatible, though they may improve behavior, add expectations, or strengthen application.

### MAJOR Compatibility
MAJOR changes may require reinterpretation, migration of usage patterns, or conscious re-reading of the doctrine.

This is especially relevant if:
- project sessions are governed over long periods
- multiple doctrine users exist
- the doctrine is embedded into tools or workflows

---

## Version Declaration Rule

The doctrine should have one officially recognized current version at all times.

That version should be declared in a visible place.

Recommended locations:
- `00_START_HERE.md`
- `18_EVOLUTION_LOG.md`

Optional additional location:
- header of major doctrine files

This is recommended for clarity.

---

## Example Version Progression

Example formation path:

- `0.1.0` — initial consolidated framework
- `0.2.0` — lifecycle and operational protocols hardened
- `0.3.0` — instruments and governance files completed
- `0.4.0` — anti-pattern and quality control strengthened
- `1.0.0` — first stable operational release after real-world validation

Example post-stable path:

- `1.0.1` — minor wording fixes
- `1.1.0` — new optional doctrine instrument added
- `1.2.0` — readiness protocol refined significantly
- `2.0.0` — lifecycle model changed materially

These are examples, not mandatory milestones.

---

## Versioning Anti-Patterns

The doctrine must avoid the following versioning failures:

### 1. Silent Semantic Drift
Changing meaning without changing version or logging impact.

### 2. Inflated Versioning
Escalating versions too aggressively for small edits.

### 3. Cosmetic Versioning
Changing versions for appearance without meaningful doctrinal change.

### 4. Hidden Structural Revision
Changing core rules while labeling the change as patch-level cleanup.

### 5. Unlogged Change Behavior
Modifying important files without recording what changed or why.

These behaviors weaken doctrine trust.

---

## Versioning Success Condition

The doctrine's versioning policy is working correctly when:

- changes are classified by real impact
- doctrine evolution remains legible over time
- foundational changes are clearly distinguished from wording fixes
- new capabilities are versioned responsibly
- semantic stability improves rather than erodes
- users of the doctrine can understand what changed and why

That is the official success condition of the versioning policy.

---

## Recommended Current State Marker

If the doctrine is still in structured formation, the recommended current line is:

`0.x.x`

This signals:
- the doctrine is real
- the doctrine is operational
- the doctrine is still maturing
- significant improvement is still expected before declaring stable release

This is the recommended posture until real doctrine application validates stability.

---

## Next File

Continue to:

`18_EVOLUTION_LOG.md`