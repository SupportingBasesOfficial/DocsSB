# DEPENDENCY MANAGEMENT PROTOCOL

## Purpose of This File

This file defines the official Dependency Management Protocol of the Engineering Work Doctrine.

Modern systems depend on third-party libraries, frameworks, and services. No production system is built from scratch. Every dependency added to a project is a piece of code written by someone else, maintained by someone else, and trusted to run inside the project's trust boundary. Supply chain attacks are real — a compromised dependency can exfiltrate secrets, inject malicious code, or open backdoors without the project's knowledge. The doctrine must govern how dependencies are evaluated, added, versioned, and updated.

This is standard practice at mega-tech companies. Dependencies are not added casually. They are evaluated against clear criteria, pinned to specific versions, locked through lockfiles, scanned for known vulnerabilities, and updated on a controlled schedule. The doctrine adopts the same standard.

This file defines:
- what criteria a dependency must meet before it is added
- how dependencies are versioned across operational states
- how dependencies are updated over time
- how dependency security is enforced
- how dependencies are recorded in the Rigid Payload
- what anti-patterns must be rejected
- when the protocol has been applied successfully

---

## Dependency Evaluation Criteria

Before adding a new dependency, the AI must evaluate it against the following criteria. A dependency that fails a critical criterion (license incompatibility, known critical vulnerability, unmaintained) must not be added in Stable state.

- **Necessity** — is this dependency truly needed, or can the functionality be implemented simply? A dependency that saves a few lines of code but pulls in thousands of lines of transitive code is a net negative. If the functionality is trivial to implement, implement it.
- **License** — is the license compatible with the project? MIT, Apache 2.0, and BSD are generally safe. GPL and AGPL may be problematic — they can impose copyleft requirements that force the project's source to be released. Evaluate license compatibility before adding, not after.
- **Security** — are there known vulnerabilities? Check CVE databases (npm audit, pip-audit, cargo audit, go vuln check, GitHub Advisory Database, OSV). A dependency with an unpatched critical or high vulnerability must not be added.
- **Maintenance** — is the dependency actively maintained? Check the last commit date, release frequency, and open issues. A dependency with no commits in over a year, no releases in over a year, or a backlog of unanswered critical issues is a risk. Unmaintained dependencies do not receive security fixes.
- **Popularity** — is it widely used? Check stars, downloads, and dependents. A dependency used by millions is more likely to have vulnerabilities found and fixed quickly. A dependency used by almost no one is a bet on an unknown.
- **Compatibility** — is it compatible with the project's language version, framework, and other dependencies? Check the dependency's requirements against the project's runtime. A dependency that forces a language version upgrade or conflicts with an existing dependency is a structural cost.
- **Transitive dependencies** — what does this dependency pull in? Every transitive dependency is also a supply chain risk. Check the full dependency tree. A small dependency that pulls in hundreds of transitive packages is a larger risk than it appears.
- **Size** — how large is the dependency? Check bundle size and install size. A dependency that adds megabytes to the bundle for minor functionality is a performance and storage cost.
- **Performance** — does it have known performance issues? Check benchmarks, issue trackers, and community reports. A dependency that is slow under load, leaks memory, or blocks the event loop is a runtime risk.
- **Documentation** — is it well-documented? Check the README, API docs, and examples. A dependency with no documentation is a maintenance burden — the team must reverse-engineer its behavior from source.
- **Alternatives** — are there better alternatives? Before adding a dependency, check if a more popular, better maintained, more secure, or more lightweight alternative exists. Adding the first dependency found without evaluating alternatives is a defect.

---

## Dependency Versioning by Operational State

How dependencies are versioned depends on the operational state of the work.

### Stable State

- **Pin exact versions.** No floating ranges (`^`, `~`, `>=`), no `latest`, no unbounded ranges. The version installed today must be the version installed tomorrow.
- **Use lockfiles.** `package-lock.json`, `yarn.lock`, `poetry.lock`, `Cargo.lock`, `go.sum` — whatever the ecosystem provides. Lockfiles must be committed to source control.
- **Never use `latest` or unbounded ranges.** `latest` means the dependency can change at any time without the project's knowledge. This is a supply chain risk and a reproducibility risk.

### Formative State

- **Ranges are acceptable.** `^` and `~` ranges allow faster iteration during active development. The lockfile still pins the resolved version.
- **Lockfiles are still used.** Even in Formative state, the lockfile ensures reproducible installs across developers and environments.

### Exploratory State

- **Whatever works is fine.** Exploratory output is throwaway. Versioning discipline is disproportionate. Install whatever version runs, and discard it when the exploration ends.

---

## Dependency Update Protocol

Dependencies are not static. They receive security fixes, bug fixes, and new features. The doctrine governs how updates are applied.

- **Regular dependency audits** — schedule a dependency audit monthly or per release cycle, whichever is shorter. The audit checks for outdated dependencies, known vulnerabilities, and abandoned dependencies. The audit is a work item, not an ad-hoc activity.
- **Security updates** — immediate. A security update is a Fix Path work item. It is not batched, not scheduled, not deferred. A known vulnerability in a Stable dependency triggers a Fix Path the moment it is discovered.
- **Minor and patch updates** — batch in a Change Path. Group minor and patch updates together, test thoroughly, and ship as a single Change Path work item. This avoids the churn of updating one dependency at a time for non-security changes.
- **Major updates** — separate work item, full Change Path. A major update may require migration, API changes, or behavior adjustments. It is its own work item with its own Rigid Payload. It is not batched with other updates.
- **Update one major dependency at a time** — do not update multiple major dependencies simultaneously. If something breaks, the team must be able to identify which update caused the break. Updating multiple majors at once makes bisection impossible.

---

## Dependency Security

Dependency security is a subset of the Security Review Protocol (`26_SECURITY_REVIEW_PROTOCOL.md`) but is critical enough to govern here explicitly.

- **Check for known vulnerabilities** — run the ecosystem's vulnerability scanner before adding any dependency and during every dependency audit:
  - Node.js: `npm audit` or `yarn audit`
  - Python: `pip-audit` or `safety check`
  - Rust: `cargo audit`
  - Go: `govulncheck`
- **Monitor for new vulnerabilities** — use Dependabot, Snyk, or an equivalent automated tool that alerts when a new CVE is published against a dependency in the project. Monitoring is continuous, not manual.
- **Critical vulnerabilities** — immediate Fix Path. No Stable dependency with a critical vulnerability remains in production past the discovery. The fix is applied, tested, and shipped as the highest priority work item.
- **High vulnerabilities** — scheduled fix within the week. A high vulnerability is not immediate, but it is not deferred to the next release cycle either. It is fixed within the current week.
- **Medium and Low vulnerabilities** — scheduled in the next release. These are tracked and addressed in the next scheduled release, not left indefinitely.

---

## Dependency and the Rigid Payload

If a work item adds, updates, or removes dependencies, the Rigid Payload's Alterações section must include a dependency record for each change. The record must state:

- **What dependencies were added, updated, or removed** — the name and action taken
- **Why** — the justification for the change. What functionality does the dependency provide? Why was it needed? Why was this dependency chosen over alternatives?
- **Version pinned** — the exact version the dependency is pinned to
- **Security check result** — what vulnerability scan was run and what it found (clean, or findings addressed)
- **License compatibility confirmed** — the dependency's license and confirmation that it is compatible with the project

A Rigid Payload that adds or updates dependencies but omits the dependency record is incomplete. The work cannot be declared 100% complete.

---

## Dependency Anti-Patterns

The following are dependency anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Adding a dependency for trivial functionality (left-pad syndrome)** — pulling in a package for something that takes a few lines of code to implement. Every dependency is a supply chain risk; trivial dependencies are risk with no payoff.
- **Using `latest` or unbounded version ranges in production** — the dependency can change at any time without the project's knowledge. This is a reproducibility risk and a supply chain risk.
- **Not using lockfiles** — without a lockfile, installs are not reproducible. Different environments may resolve different versions, leading to inconsistent behavior and undiagnosable bugs.
- **Ignoring security vulnerabilities** — a known vulnerability in a dependency that is left unaddressed. This is a security defect, not a technical debt item.
- **Not checking transitive dependencies** — evaluating only the direct dependency while ignoring what it pulls in. The transitive tree is where supply chain attacks often hide.
- **Adding dependencies without evaluating alternatives** — taking the first dependency found without comparing against alternatives. A better option may exist that is lighter, safer, or better maintained.
- **Updating multiple major dependencies simultaneously** — if something breaks, the team cannot identify which update caused it. Major updates are isolated, one at a time.

---

## Dependencies and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that all dependencies are pinned to exact versions, lockfiles are committed, and a security scan is clean. No work enters Stable state with unpinned or vulnerable dependencies.

---

## Protocol Success Condition

The Dependency Management Protocol has been applied successfully when:

- every dependency in Stable state has been evaluated against all criteria before being added
- every dependency in Stable state is pinned to an exact version
- every dependency in Stable state is locked through a committed lockfile
- every dependency in Stable state has been security-checked and found clean or had findings addressed
- every dependency addition, update, or removal is documented in the Rigid Payload with justification, version, security check result, and license confirmation
- no dependency anti-pattern is present in the delivered output

That is the official success condition of the Dependency Management Protocol.

**Anti-pattern:** See ANTI-PATTERN 36 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.7 in `08_DECISION_RULES.md`.

---

## Next File

Continue to:

`29_DOCUMENTATION_PROTOCOL.md`
