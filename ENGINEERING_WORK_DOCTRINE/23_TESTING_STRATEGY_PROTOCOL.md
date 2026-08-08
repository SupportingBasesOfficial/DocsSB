# TESTING STRATEGY PROTOCOL

## Purpose of This File

The doctrine states "100% as Floor" but does not define what types of tests constitute that 100%. This protocol defines what constitutes "100% verified" for each work type and operational state. Without a concrete definition, "100% verified" is an unenforceable slogan. This file makes it enforceable by binding each work type and operational state to a specific set of required test types.

---

## Test Type Taxonomy

1. **Unit tests** — Verify individual function or class behavior in isolation. Dependencies are mocked or stubbed. These are the fastest and most numerous tests.
2. **Integration tests** — Verify component interaction. Multiple units are wired together with real (or near-real) dependencies to confirm they cooperate correctly.
3. **End-to-end (E2E) tests** — Verify full user flows from entry to exit. These exercise the entire system as a user would, including UI, API, database, and external integrations.
4. **Contract tests** — Verify API/interface contracts between services. Each side of a boundary is tested against a shared contract so that breaking changes are caught before deployment.
5. **Performance tests** — Verify latency, throughput, and resource usage under load. These confirm the system meets non-functional performance requirements.
6. **Security tests** — Verify vulnerability scanning, authentication/authorization, and input validation. These confirm the system resists known attack classes.
7. **Chaos tests** — Verify resilience through failure injection. Dependencies are killed, degraded, or delayed to confirm the system fails gracefully.
8. **Characterization tests** — Capture current behavior as-is, without asserting correctness. Used when refactoring code that has no existing tests, so that behavior is preserved.

---

## Test Requirements by Work Type

| Work Type | Required Test Types |
|---|---|
| Project | unit + integration + e2e + contract + performance + security (in Stable) |
| Feature | unit + integration + e2e (in Stable); unit + integration (in Formative) |
| Refactoring | characterization + unit + integration (always); e2e if behavior is user-visible |
| Bugfix | regression test (the test that would have caught the bug) + unit |
| Task | unit (if logic); none (if config) |
| Question | none |

---

## Test Requirements by Operational State

1. **Exploratory** — No tests required. Exploratory work is throwaway by definition. Tests are not mandated, but characterization tests may be written if the exploration is being captured for future use.
2. **Formative** — Tests are required when committing. Characterization tests are required for refactoring. The bar is "tests exist for committed code," not "full suite passes."
3. **Stable** — The full test suite per work type requirements (see table above) must pass. This is the state in which "100% verified" is enforceable.

---

## Coverage Standards

"100% coverage" does not mean line coverage. It means behavior coverage. Specifically:

1. **Not line coverage** — Chasing 100% line coverage produces tests that execute code without asserting behavior. The target is behavior coverage, not metric coverage.
2. **Every public function must have at least one test** — A public function with no test is unverified by definition.
3. **Every branching path must be tested** — Each branch (if/else, switch case, loop entry/exit) must have a test that exercises it.
4. **Every error/exception path must be tested** — Happy paths are not enough. Every documented error and exception path must have a test that triggers and asserts it.
5. **Integration points must have contract tests** — Every boundary between services or modules must have a contract test that pins the interface.
6. **Critical paths must have e2e tests** — The paths that users depend on most must be covered by end-to-end tests that confirm the full flow works.

---

## Test Quality Standards

1. **Tests must be deterministic** — No flaky tests. A test that passes sometimes and fails sometimes is a defect, not a test. Time, randomness, network, and external state must be controlled or mocked.
2. **Tests must be independent** — No test order dependency. Each test must set up and tear down its own state. A test must not rely on another test having run first.
3. **Tests must be fast** — Unit tests <1s each. Integration tests <10s each. E2E tests <60s each. Tests that exceed these limits either belong in a slower tier or need optimization.
4. **Tests must be maintainable** — Clear, readable, single responsibility. A test should test one behavior. If a test is hard to read, it is a liability.
5. **Tests must be self-documenting** — The test name describes the behavior being verified. A reader should understand what the test asserts from its name alone, without reading the body.

---

## Test Pyramid

The doctrine follows the test pyramid:

1. **70% unit tests** — Fast, isolated, many. These are the foundation. Most behavior is verified here.
2. **20% integration tests** — Slower, component interaction, fewer. These confirm that units cooperate.
3. **10% e2e tests** — Slowest, full flow, fewest. These confirm that the system works end to end for critical paths.
4. **Performance, security, chaos tests are separate concerns** — These do not fit the pyramid. They are run on their own schedules and have their own pass/fail criteria.

---

## When Tests Don't Exist

When refactoring code that has no existing tests, do not refactor blind. Write characterization tests first to capture the current behavior, then refactor under their protection. This is the Refactoring Without Tests protocol defined in `09_OUTPUT_QUALITY_STANDARD.md`. Characterization tests do not assert correctness — they assert that behavior did not change.

---

## Test-Driven vs Test-After

The doctrine does not mandate TDD. It mandates that tests exist before work is declared 100%. The timing of test creation depends on operational state:

1. **In Formative state** — Tests may come after implementation. The code is still taking shape, and premature tests may be discarded. The requirement is that tests exist when the code is committed.
2. **In Stable state** — Tests should come before or during implementation. The system is stable enough that behavior is predictable, and tests-first or tests-during reduces rework.

In both states, the final condition is the same: the required test types must exist and pass before the work item is declared 100% verified.

---

## Testing in the Rigid Payload

The Rigid Payload (defined in `20_ENFORCEMENT_LAYER.md`) has four sections. Testing results go in the **Enforcement** section — testing is verification, not a change.

The Enforcement section must state:
- **Which test types were run** — unit, integration, e2e, contract, performance, security, chaos, characterization (as applicable to the work type)
- **Results of each test type** — pass/fail, with coverage numbers where applicable
- **100% criterion confirmation** — that all required test types for the work type and operational state pass

If a work type does not require tests (e.g., Question), the Enforcement section must state: "No tests required — work type does not require testing."

This ensures that testing is not silently skipped. It must be explicitly accounted for in every work item's delivery record.

---

## Testing Anti-Patterns

The following are testing anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Testing theater** — tests that look comprehensive but verify nothing meaningful. High coverage percentage with tests that don't assert behavior, or tests that only test the implementation (not the contract).
- **No characterization tests for refactoring** — refactoring without first writing characterization tests that capture current behavior. Without a baseline, equivalence cannot be proven.
- **Testing only the happy path** — tests that only verify the expected flow. Error paths, edge cases, boundary conditions, and failure modes are untested.
- **Integration tests for everything** — using integration tests where unit tests would be faster, more precise, and more diagnostic. Integration tests have their place, but they should not be the only test type.
- **No mutation testing for refactoring** — refactoring without mutation testing. Tests that pass before and after refactoring may not actually detect mutations — they may be testing nothing meaningful.
- **Skipping tests "for now"** — deferring test writing to "later" in Stable state. In Stable state, tests are written with the code, not after.
- **Testing implementation details instead of behavior** — tests that break when the implementation changes but the behavior doesn't. These tests constrain refactoring without verifying correctness.

---

## Testing and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that tests be written for the stabilized code (characterization tests, unit tests, integration tests as appropriate). No work enters Stable state without the testing foundation in place.

---

## Protocol Success Condition

The testing strategy has been applied successfully when:

1. Every work item in Stable state has the required test types passing, per the work type table.
2. "100% verified" has a concrete, test-type-specific meaning — not a slogan, but a checklist of test types that must be green.
3. No work item is declared 100% verified while missing a required test type for its work type and operational state.

The Test Gate (see `31_QUALITY_GATES.md`) enforces these testing requirements at stage transitions — no work item advances past a gate without the required test types passing for its work type and operational state.

**Anti-pattern:** See ANTI-PATTERN 31 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.2 in `08_DECISION_RULES.md`.

---

## Next File

`24_ARCHITECTURE_DECISION_RECORDS.md`
