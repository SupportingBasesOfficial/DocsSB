# SECURITY REVIEW PROTOCOL

## Purpose of This File

This file defines the official Security Review Protocol of the Engineering Work Doctrine.

Its purpose is to ensure that work output is **security-reviewed before being declared 100% in Stable state**.

The doctrine surfaces security concerns during discovery (Discovery Dimension Protocol, Category 1 — Safety and Criticality). But surfacing is not enough. A work item can surface a security concern during discovery and still ship with a vulnerability. Surfacing is the first step; review is the closing step.

This is standard practice at mega-tech companies. Security review is mandatory for changes to sensitive systems. A change to authentication, authorization, data access, or external interfaces does not ship without a security review sign-off. The doctrine adopts the same standard.

This file defines:
- what security review covers
- what levels of security review exist
- when each level is required
- how security review is recorded in the Rigid Payload
- what anti-patterns must be rejected
- when the protocol has been applied successfully

---

## Security Review Scope

Security review covers the following areas. Each area must be checked at the level appropriate to the work.

- **Authentication** — how users and services are verified. Are credentials stored correctly? Are sessions managed securely? Is multi-factor authentication supported where required?
- **Authorization** — how access is granted and checked. Is every privileged action guarded by an access check? Are privilege escalation paths closed? Is the principle of least privilege enforced?
- **Input validation** — all external input is validated. Input from users, APIs, files, environment variables, and network sources is treated as untrusted until validated.
- **Output encoding** — all output is encoded to prevent injection. Output sent to browsers, shells, databases, interpreters, or logs is encoded for the target context.
- **Data protection** — sensitive data is encrypted at rest and in transit. Encryption keys are managed through a secrets manager, not hardcoded.
- **Secret management** — no secrets in code, logs, or config files. API keys, passwords, tokens, and private keys are loaded from a secrets manager or environment variables, never committed to source control.
- **Dependency vulnerabilities** — known CVEs in dependencies are identified and addressed. Dependencies are pinned to safe versions.
- **Error handling** — errors do not leak sensitive information. Stack traces, internal paths, database schema details, and secret values are not exposed to end users or in logs.
- **Rate limiting** — protection against abuse and denial-of-service. Public endpoints are rate-limited. Expensive operations are bounded.
- **Audit trails** — security-relevant actions are logged. Authentication events, authorization changes, data access, and administrative actions are recorded with sufficient detail for incident response.

---

## Security Review Levels

Security review is not binary. It scales with the risk of the work. The doctrine defines three levels.

### Level 1 — Automated

Automated security scanning. This includes:

- **SAST** (Static Application Security Testing) — scans source code for known vulnerability patterns
- **DAST** (Dynamic Application Security Testing) — scans running services for exposed vulnerabilities
- **Dependency scanning** — checks dependencies against known CVE databases
- **Secret scanning** — checks repositories and artifacts for committed secrets

**Required for all Stable work.** No Stable work item is complete without Level 1 passing.

### Level 2 — Manual Review

Human or AI review of security-relevant code. This goes beyond what automated tools can detect. It covers:

- logic flaws in authorization checks
- insecure data flows that tools cannot trace
- business-logic vulnerabilities
- contextual risks specific to the system

**Required for work that touches authentication, authorization, data access, or external interfaces.** If the work changes how identities are verified, how access is granted, how sensitive data is read or written, or how the system interacts with external callers, Level 2 is mandatory.

### Level 3 — Threat Model

Systematic threat modeling using STRIDE or an equivalent framework. This covers:

- spoofing, tampering, repudiation, information disclosure, denial of service, elevation of privilege
- attack surfaces and trust boundaries
- data flow analysis across trust domains
- residual risk acceptance by the responsible party

**Required for new systems, major architecture changes, or systems handling sensitive data.** If the work creates a new system, changes the architecture of an existing system, or handles data classified as sensitive, Level 3 is mandatory.

---

## Security Review by Operational State

Security review depth scales with the operational state of the work.

| Operational State | Security Review Requirement |
|---|---|
| Exploratory | Not required. Exploratory output is throwaway. Security review would be disproportionate. |
| Formative | Level 1 when committing. Formative code may be committed to a branch, and that branch must pass automated security scanning. Full review is deferred until the work stabilizes. |
| Stable | Level 1 always. Level 2 for security-relevant changes. Level 3 for new systems or major changes. |

A work item cannot transition to Stable state without the required security review level being applied and documented.

---

## Security Review in the Rigid Payload

The Rigid Payload (defined in `20_ENFORCEMENT_LAYER.md`) has four sections: Diagnóstico, Alterações, Enforcement, Rollback. Security review touches two sections:

- **Alterações** — what security-relevant code was changed (input validation added, auth checks modified, encryption updated). This is a record of what changed, like any other code change.
- **Enforcement** — how security was verified (what review level was applied, what was checked, what tools were used, what vulnerabilities were found and how they were addressed, what residual risk remains).

The Enforcement section must state:

- **What security review level was applied** — Level 1, Level 2, Level 3, or a combination
- **What was checked** — which scope areas were reviewed and which tools or methods were used
- **What vulnerabilities were found and how they were addressed** — each finding, its severity, and the fix or mitigation applied
- **What residual risk remains** — any accepted risk, with the reason for acceptance and the party that accepted it

A Rigid Payload that omits the security review information in the Enforcement section is incomplete. The work cannot be declared 100% complete.

---

## OWASP Top 10 Checklist

For web-facing work — any work that exposes an HTTP endpoint, renders content in a browser, or processes input from a web client — the AI must check the OWASP Top 10:

- **Injection** — SQL injection, NoSQL injection, command injection, LDAP injection. All user-controlled input is parameterized or validated before being passed to interpreters.
- **Broken Authentication** — session management is secure, credentials are stored with strong hashing, session tokens are rotated, login is protected against brute force.
- **Sensitive Data Exposure** — sensitive data is encrypted in transit (TLS) and at rest, no sensitive data in URLs or logs, strong ciphers are used.
- **XML External Entities (XXE)** — XML parsers disable external entity resolution, or XML processing is avoided for untrusted input.
- **Broken Access Control** — every privileged action enforces an access check, direct object references are protected, horizontal and vertical privilege escalation are prevented.
- **Security Misconfiguration** — default credentials are changed, error messages are non-verbose, unnecessary features are disabled, security headers are set.
- **Cross-Site Scripting (XSS)** — all user-controlled output is context-encoded, Content Security Policy is set, input is sanitized where encoding is insufficient.
- **Insecure Deserialization** — deserialization of untrusted data is avoided, integrity checks are applied, or safe serialization formats are used.
- **Using Components with Known Vulnerabilities** — dependencies are scanned for CVEs, vulnerable dependencies are upgraded or replaced, versions are pinned.
- **Insufficient Logging & Monitoring** — security-relevant events are logged, logs are protected against tampering, alerts are configured for suspicious activity.

For non-web work, the OWASP Top 10 does not apply directly, but the equivalent concerns (injection, access control, data exposure, dependency vulnerabilities, logging) still apply and must be checked under the relevant scope areas.

---

## Security Anti-Patterns

The following are security anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Hardcoded secrets** — API keys, passwords, tokens, or private keys committed to source control, embedded in config files, or written to logs.
- **Unvalidated input** — external input used without validation, whether from users, APIs, files, environment, or network.
- **Overly permissive CORS** — `Access-Control-Allow-Origin: *` combined with credentials, or wildcard origins on sensitive endpoints.
- **Missing rate limiting** — public or expensive endpoints with no rate limit, allowing abuse or denial of service.
- **Verbose error messages that leak internals** — stack traces, database schema, internal paths, or secret values returned to end users or written to application logs.
- **Unencrypted sensitive data** — sensitive data stored or transmitted in plaintext, or encrypted with weak or deprecated ciphers.
- **Missing audit trails for security actions** — authentication, authorization, data access, or administrative actions not logged, or logs not protected against tampering.

---

## Security Review and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that security review is completed at the appropriate level (Level 1 automated, Level 2 manual if touching auth/data/external interfaces, Level 3 threat model if new system or major change). No work enters Stable state without security review.

---

## Protocol Success Condition

The Security Review Protocol has been applied successfully when:

- every Stable work item has been security-reviewed at the appropriate level
- the level applied matches the work's risk profile (Level 1 for all, Level 2 for security-relevant, Level 3 for new systems or major changes)
- the Rigid Payload documents what level was applied, what was checked, what vulnerabilities were found and addressed, and what residual risk remains
- no security anti-pattern is present in the delivered output
- for web-facing work, the OWASP Top 10 checklist has been completed

That is the official success condition of the Security Review Protocol.

Dependency security scanning (see `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md`) is part of the security review — dependencies must be evaluated per `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md` before security review can be declared complete. Additionally, for work that touches data, data classification and handling rules (see `33_DATA_GOVERNANCE_PROTOCOL.md`) must be verified during security review to ensure data protection measures are correctly applied.

**Anti-pattern:** See ANTI-PATTERN 34 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.5 in `08_DECISION_RULES.md`.

---

## Next File

Continue to:

`27_TECHNICAL_DEBT_PROTOCOL.md`
