# DISCOVERY DIMENSION PROTOCOL

## Purpose of This File

This file defines the official Discovery Dimension Protocol of the Engineering Work Doctrine.

Its purpose is to ensure that discovery **systematically covers all dimensions that could materially affect the work**, regardless of domain.

The doctrine is universal in method (Principle 20). It does not contain domain-specific solutions for healthcare, aviation, ML, embedded systems, or any other specialized field. That is correct — the doctrine should not be an encyclopedia of domain knowledge.

However, the doctrine **must guarantee that discovery is complete**. If a work item has safety-critical implications, compliance requirements, non-functional constraints, or domain-specific concerns, these must be surfaced during discovery — not discovered after delivery.

This file provides the protocol that ensures this completeness. It is a **dimension checklist**, not a domain knowledge base. For each dimension, the protocol tells the AI: **check whether this applies, and if so, surface it during discovery.**

---

## How This Protocol Works

During discovery (Stage 1 of any lifecycle path), the AI must run through the dimension categories defined in this file. For each category:

1. **Check** — Does this dimension apply to the work?
2. **Surface** — If yes, raise it explicitly in the discovery output
3. **Classify** — Is it a confirmed requirement, a plausible dimension, or not applicable?
4. **Incorporate** — If confirmed or plausible, incorporate it into the work agreement

This protocol does NOT replace the existing discovery protocol (`04_DISCOVERY_PROTOCOL.md`) or the brownfield discovery protocol (`15_BROWNFIELD_DISCOVERY_PROTOCOL.md`). It **extends** them by ensuring no dimension is missed.

The protocol applies to all work types, but its depth scales with the work type and operational state:
- **Project (Full Lifecycle):** All dimensions checked systematically
- **Feature (Feature Path):** Dimensions relevant to the feature's domain checked
- **Refactoring (Change Path):** Dimensions that could be affected by the change checked
- **Bugfix (Fix Path):** Dimensions relevant to the bug's impact area checked
- **Task (Light Path):** Quick scan of dimensions
- **Question (Direct Path):** Dimensions mentioned if directly relevant to the answer

In **Exploratory** state, this protocol is minimal — only check dimensions that affect the viability question.
In **Formative** state, check dimensions that could affect the shape being discovered.
In **Stable** state, full dimension check is mandatory.

---

## Dimension Category 1 — Safety and Criticality

### When to Check
For any system where failure could cause physical harm, financial loss, data loss, or operational disruption.

### Dimensions to Surface

- **Safety-critical classification:** Is this a system where failure could cause injury or death? (medical devices, avionics, automotive, industrial control)
- **Mission-critical classification:** Is this a system where failure could cause severe operational disruption? (emergency services, financial infrastructure, power grid)
- **Safety certification requirements:** Does the system require formal safety certification? (DO-178C for aviation, IEC 62304 for medical, ISO 26262 for automotive)
- **Failure mode severity:** What is the worst-case outcome of a failure? (data loss, financial loss, service outage, physical harm)
- **Fail-safe requirements:** Must the system fail in a safe state? What happens on partial failure?
- **Redundancy requirements:** Does the system require redundant components for safety?

### If Any Dimension Applies

The work agreement must include:
- safety classification level
- certification requirements (if any)
- failure mode analysis
- fail-safe behavior specification
- redundancy requirements (if any)

The AI must not proceed to build without confirming how safety-critical concerns are addressed. In Stable state, safety-critical dimensions are **blocking lacunae** until resolved.

---

## Dimension Category 2 — Compliance and Regulatory

### When to Check
For any system that handles personal data, financial data, health data, or operates in a regulated industry.

### Dimensions to Surface

- **Data protection regulations:** Does the system handle personal data subject to GDPR, CCPA, LGPD, or other data protection laws?
- **Healthcare compliance:** Does the system handle health data subject to HIPAA, HITECH, or equivalent?
- **Financial compliance:** Does the system handle payment data subject to PCI-DSS, or operate as a financial service subject to SOX, AML, or KYC regulations?
- **Multi-compliance:** Does the system need to comply with multiple regulatory frameworks simultaneously? (e.g., SOC2 + HIPAA + GDPR)
- **Data residency:** Does the system have data residency requirements? (data must stay in a specific country/region)
- **Audit requirements:** Does the system require audit trails, immutable logs, or compliance reporting?
- **Right to be forgotten:** Does the system need to support data deletion requests?
- **Data retention policies:** Are there mandatory data retention periods?

### If Any Dimension Applies

The work agreement must include:
- applicable regulatory frameworks
- data classification scheme
- audit trail requirements
- data residency constraints
- retention and deletion policies
- compliance reporting requirements (if any)

Multi-compliance situations require explicit mapping of which frameworks apply to which data flows. The AI must not assume that satisfying one framework satisfies all.

---

## Dimension Category 3 — Non-Functional Requirements

### When to Check
For any system with performance, scalability, reliability, or consistency requirements beyond basic functionality.

### Dimensions to Surface

- **Service Level Objectives (SLOs):** Are there defined uptime, latency, or throughput targets? (e.g., 99.99% uptime, <100ms p99 latency)
- **Service Level Agreements (SLAs):** Are there contractual obligations to customers with penalties for breach?
- **Scalability targets:** What are the expected load patterns? (users per day, requests per second, data volume per month)
- **Consistency model:** Does the system require strong consistency, eventual consistency, or causal consistency? Are there specific consistency guarantees for specific operations?
- **Latency budgets:** Are there end-to-end latency budgets? (e.g., user action must complete in <500ms, of which API is <100ms, DB is <50ms)
- **Throughput targets:** Are there minimum throughput requirements? (e.g., 10k transactions per second)
- **Availability targets:** Are there availability requirements? (e.g., 99.9%, 99.99%, 99.999%)
- **Durability targets:** Are there data durability requirements? (e.g., 11 nines for object storage)
- **Recovery objectives:** RTO (Recovery Time Objective) and RPO (Recovery Point Objective)?

### If Any Dimension Applies

The work agreement must include:
- SLO/SLA definitions
- performance budgets (latency, throughput, resource usage)
- scalability targets
- consistency model
- availability and durability targets
- RTO and RPO

Performance budgets must be explicit and allocated across system components. The AI must not design a system without knowing whether it needs to handle 10 or 10 million requests per second.

---

## Dimension Category 4 — Hardware and Environmental Constraints

### When to Check
For embedded systems, IoT, mobile applications, edge computing, or any system with hardware constraints.

### Dimensions to Surface

- **Memory constraints:** Is there a memory budget? (embedded systems, mobile apps)
- **CPU constraints:** Is there a CPU budget or processing power limitation?
- **Storage constraints:** Is there a storage budget? (flash, disk, network storage)
- **Power constraints:** Is there a power consumption budget? (battery-powered devices)
- **Network constraints:** Is there limited or intermittent connectivity? (IoT, edge, offline-first)
- **Environmental constraints:** Does the system operate in extreme conditions? (temperature, vibration, radiation)
- **Hardware interfaces:** Does the system need to interface with specific hardware? (sensors, actuators, custom hardware)
- **Real-time constraints:** Does the system have hard real-time deadlines? (control systems, signal processing)
- **Form factor constraints:** Are there physical size or weight limitations?

### If Any Dimension Applies

The work agreement must include:
- hardware constraints budget (memory, CPU, storage, power)
- network connectivity assumptions
- real-time deadlines (if any)
- hardware interface specifications
- environmental operating conditions

The AI must not design an embedded system without knowing whether it has 4KB or 4GB of RAM.

---

## Dimension Category 5 — Machine Learning Specifics

### When to Check
For any system that involves machine learning, AI models, data pipelines, or automated decision-making.

### Dimensions to Surface

- **Model lifecycle:** How are models trained, validated, deployed, and monitored?
- **Data pipeline:** How is training data collected, cleaned, labeled, versioned, and validated?
- **Model versioning:** How are model versions tracked, compared, and rolled back?
- **Data drift detection:** How is the system monitored for data drift (input distribution changes) and concept drift (output relationship changes)?
- **A/B testing framework:** Is there a framework for comparing model versions in production?
- **Model explainability:** Does the system need to explain its decisions? (regulatory requirement, user trust, debugging)
- **Bias and fairness:** Are there fairness requirements? How is bias measured and mitigated?
- **Training infrastructure:** What compute resources are needed for training? (GPU, TPU, distributed training)
- **Inference latency:** What is the latency budget for model inference?
- **Feedback loop:** How does the system collect feedback to improve the model?
- **Human-in-the-loop:** Does the system require human review for certain decisions?
- **Safety guardrails:** Are there guardrails to prevent harmful model outputs?

### If Any Dimension Applies

The work agreement must include:
- model lifecycle definition
- data pipeline architecture
- model versioning strategy
- drift monitoring protocol
- explainability requirements (if any)
- fairness requirements (if any)
- inference latency budget
- feedback loop design
- human-in-the-loop points (if any)
- safety guardrails (if any)

ML systems have unique lifecycle concerns that traditional software does not. The AI must surface these during discovery, not discover them after deployment.

---

## Dimension Category 6 — Large-Scale Migration

### When to Check
For any work that involves migrating a system from one architecture to another (monolith to microservices, REST to GraphQL, one framework to another, on-premise to cloud).

### Dimensions to Surface

- **Migration strategy:** Is this a big-bang migration or incremental? (incremental is strongly preferred)
- **Incremental migration plan:** If incremental, what is the sequence? Which components migrate first? What is the strangler-fig pattern application?
- **Coexistence period:** Will the old and new systems coexist during migration? How long? How do they communicate?
- **Data migration:** How is data migrated? Is it a one-time copy or continuous sync? What about data that changes during migration?
- **Rollback plan:** Can the migration be rolled back at each step? What is the cost of rollback at each stage?
- **Risk assessment:** What is the riskiest part of the migration? What can go wrong?
- **Testing strategy:** How is equivalence verified at each step? (characterization tests, parallel running, shadow traffic)
- **Cutover plan:** What is the plan for switching from old to new? Is it gradual or instantaneous?
- **Team capacity:** Does the team have capacity for migration alongside feature work?
- **Business continuity:** Can the business operate normally during migration, or is there a freeze period?

### If Any Dimension Applies

The work agreement must include:
- migration strategy (incremental vs big-bang, with justification)
- migration sequence and dependencies
- coexistence architecture (if applicable)
- data migration plan
- rollback plan at each step
- testing strategy for equivalence verification
- cutover plan
- business continuity plan

Large-scale migrations are among the riskiest engineering work. The AI must not treat them as simple refactoring — they require their own discovery depth within the Change Path.

---

## Dimension Category 7 — Large-Scale Legacy Systems

### When to Check
For any work on a system with: >100k lines of code, >10 developers, >5 years of age, or significant accumulated technical debt.

### Dimensions to Surface

- **System understanding:** How well is the system understood? Is there documentation? Are there people who understand it?
- **Technical debt inventory:** What is the state of technical debt? Is it tracked? Is there a prioritization?
- **Risk hotspot mapping:** Which parts of the system are highest-risk? (most changed, most bugs, most coupled, least understood)
- **Change frequency:** Which parts change most frequently? These are higher-priority for stabilization.
- **Business criticality mapping:** Which parts are most business-critical? These require more careful changes.
- **Dependency mapping:** What are the critical dependencies? What depends on what?
- **Test coverage reality:** What is the actual test coverage? Where are the gaps?
- **Knowledge distribution:** Is knowledge concentrated in one person, or distributed across the team?
- **Prioritization framework:** How should work be prioritized? (risk × frequency × criticality)
- **Incremental improvement plan:** Can the system be improved incrementally, or does it require a rewrite?

### If Any Dimension Applies

The work agreement must include:
- system understanding assessment
- risk hotspot map
- prioritization framework (risk × frequency × criticality)
- incremental improvement plan
- knowledge distribution assessment
- test coverage gap analysis

Large-scale legacy systems require **prioritization** — you cannot fix everything at once. The AI must help the user prioritize based on risk, frequency, and criticality, not just "what seems most broken."

---

## Dimension Category 8 — Multi-Team Coordination

### When to Check
For any work that involves multiple teams, multiple AI instances, or distributed contributors working on the same system.

### Dimensions to Surface

- **Team boundaries:** Which teams own which parts of the system? Are boundaries clear?
- **Interface contracts:** What are the contracts between teams? Are they explicit? Are they versioned?
- **Change coordination:** How are cross-team changes coordinated? Is there a change advisory process?
- **State sharing:** How do teams share state? (shared documentation, shared work state files, regular syncs)
- **Conflict prevention:** How are conflicts prevented? (ownership models, branch strategies, merge protocols)
- **Dependency awareness:** Does each team know what depends on their work? Do they know what they depend on?
- **Communication protocol:** How do teams communicate about changes? (async, sync, documentation, alerts)
- **Shared infrastructure:** Is there shared infrastructure? How is it governed?
- **Onboarding:** How do new team members or new AI instances get context?

### If Any Dimension Applies

The work agreement must include:
- team ownership map
- interface contract definitions
- change coordination protocol
- state sharing mechanism
- conflict prevention strategy
- dependency awareness documentation
- communication protocol

Multi-team coordination is a doctrinal concern because it affects **state consistency** — the doctrine's guarantees depend on each work item having a clear state, classification, and owner. Without coordination, multiple teams can unknowingly work on the same item with different states and classifications.

See `13_PROJECT_SESSION_TEMPLATE.md` — Multi-Team Coordination Protocol for the full protocol.

---

## Mega-Tech Discovery Dimensions (Categories 9–13)

Categories 9 through 13 cover the mega-tech protocol concerns that must be discovered during production-grade work: security, observability, data governance, testing strategy, and dependency landscape.

These dimensions are **particularly relevant for Stable state work**. In Stable state, a full check of all five categories is mandatory — they are not optional refinements but core discovery requirements for any system that will run in production.

In **Formative** state, these dimensions are checked lightly — only enough to ensure the shape being discovered does not conflict with known security, observability, governance, testing, or dependency constraints.

In **Exploratory** state, these dimensions are generally **skipped** — the viability question rarely depends on them. They should only be checked if the viability question itself hinges on one of these concerns (e.g., a security feasibility question, a dependency availability question).

---

## Dimension Category 9 — Security and Threat Model

### When to Check
For any system that handles authentication, authorization, sensitive data, network exposure, or operates in an environment with adversarial threats.

### Dimensions to Surface

- **Threat model:** What is the threat model? Who are the adversaries? What are their capabilities and motivations? (external attackers, insider threats, supply chain attackers)
- **Authentication requirements:** How are users and services authenticated? (passwords, OAuth, SAML, mTLS, API keys, service accounts)
- **Authorization requirements:** How are access permissions enforced? (RBAC, ABAC, ACLs, policy engines) What is the granularity? (resource-level, operation-level, field-level)
- **Data protection:** What data needs protection? At rest? In transit? In use? What encryption standards apply? (AES-256, TLS 1.3)
- **Secret management:** How are secrets (API keys, passwords, certificates) stored, rotated, and accessed? (vault, KMS, env vars)
- **Input validation:** What input validation is required? (SQL injection, XSS, CSRF, command injection protections)
- **Attack surface:** What is the system's attack surface? (public APIs, web endpoints, internal services, file uploads)
- **Security boundaries:** What are the trust boundaries? Where is data declassified or re-validated as it crosses boundaries?
- **Vulnerability management:** Is there a vulnerability scanning and patching process? What is the SLA for critical vulnerabilities?
- **Compliance-driven security:** Are there security frameworks that apply? (OWASP Top 10, NIST 800-53, CIS benchmarks)

### If Any Dimension Applies

The work agreement must include:
- threat model definition
- authentication and authorization scheme
- data protection requirements (encryption at rest, in transit, in use)
- secret management strategy
- input validation requirements
- attack surface inventory
- security boundary map
- vulnerability management process

Security requirements discovered late are the most expensive to retrofit. The AI must surface security dimensions during discovery, not after implementation. See `26_SECURITY_REVIEW_PROTOCOL.md` for the full security review protocol.

---

## Dimension Category 10 — Observability Requirements

### When to Check
For any system that will run in production, or any system where understanding runtime behavior is necessary for debugging, alerting, or performance analysis.

### Dimensions to Surface

- **Logging requirements:** What events must be logged? What log level structure? What fields are mandatory? (timestamp, trace ID, user ID, request ID)
- **Metrics requirements:** What metrics must be captured? (counters, gauges, histograms, summaries) What are the key business and operational metrics?
- **Tracing requirements:** Is distributed tracing required? What trace context propagation is needed? (W3C Trace Context, B3)
- **Alerting requirements:** What conditions must trigger alerts? What are the alert severity levels? What are the notification channels? (PagerDuty, Slack, email)
- **Dashboard requirements:** What dashboards are needed? Who are the audiences? (engineering, operations, business, executive)
- **SLO monitoring:** Are SLOs being tracked? What is the burn rate? Are there error budget alerts?
- **Audit logging:** Are there audit log requirements? (immutable, tamper-evident, retention-bound)
- **Structured logging:** Does the system require structured logs? (JSON, key-value) What schema?
- **Log aggregation:** Where do logs go? (ELK, Splunk, CloudWatch, Datadog) What is the retention?
- **Sampling strategy:** Is sampling needed for high-volume telemetry? What is the sampling rate?

### If Any Dimension Applies

The work agreement must include:
- logging requirements (events, levels, fields, schema)
- metrics requirements (names, types, labels)
- tracing requirements (if applicable)
- alerting requirements (conditions, severity, channels)
- dashboard requirements (audiences, metrics displayed)
- SLO monitoring plan (if SLOs are defined)
- audit logging requirements (if applicable)
- log aggregation and retention strategy

Observability is not an add-on — it is a design-time concern. The AI must not design a system without knowing how its runtime behavior will be understood. See `25_OBSERVABILITY_PROTOCOL.md` for the full observability protocol.

---

## Dimension Category 11 — Data Governance Landscape

### When to Check
For any system that creates, reads, updates, or deletes data — particularly data with classification, retention, lineage, or compliance requirements.

### Dimensions to Surface

- **Data inventory:** What data does the work touch? What data is created, modified, read, or deleted?
- **Data classification:** What is the classification of each data element? (public, internal, confidential, restricted, PII, PHI, PCI)
- **Data lineage:** Where does the data come from? Where does it go? What transformations occur?
- **Data retention:** What are the retention requirements for each data type? (legal minimums, business maximums, deletion schedules)
- **Data deletion:** How is data deleted? Is deletion hard or soft? Is there a right-to-be-forgotten requirement?
- **Data access controls:** Who can access what data? Are access controls enforced at the application, database, or both?
- **Data quality:** Are there data quality requirements? (accuracy, completeness, timeliness, consistency)
- **Data ownership:** Who owns each data domain? Who is the data steward?
- **Data sharing:** Is data shared with other systems or teams? Under what agreements? What are the constraints?
- **Data migration impact:** Does the work require data migration? What is the impact on existing data?

### If Any Dimension Applies

The work agreement must include:
- data inventory with classification
- data lineage map
- retention and deletion requirements per data type
- data access control requirements
- data quality requirements (if any)
- data ownership and stewardship
- data sharing agreements and constraints (if any)

Data governance is a discovery concern because it affects schema design, access patterns, retention policies, and compliance — all of which are expensive to change after implementation. See `33_DATA_GOVERNANCE_PROTOCOL.md` for the full data governance protocol.

---

## Dimension Category 12 — Testing Strategy Requirements

### When to Check
For any system that requires verification of correctness, safety, performance, or behavioral contracts — which is, in practice, all production systems.

### Dimensions to Surface

- **Test types required:** What test types are needed? (unit, integration, end-to-end, contract, performance, load, chaos, security, accessibility)
- **Coverage targets:** What are the coverage targets? (line coverage, branch coverage, path coverage, mutation testing) Are they enforced?
- **Test infrastructure:** What test infrastructure exists? (test runners, CI pipelines, test environments, test data management)
- **Test data:** How is test data generated and managed? (synthetic data, anonymized production data, fixtures, factories)
- **Test environments:** What test environments exist? (local, CI, staging, pre-prod) How do they differ from production?
- **Performance testing:** Are there performance test requirements? (load testing, stress testing, soak testing, spike testing)
- **Contract testing:** Are there consumer-driven contract tests? (Pact, Spring Cloud Contract) Who are the consumers and providers?
- **Regression strategy:** How are regressions prevented? (characterization tests, golden master tests, snapshot tests)
- **Flaky test tolerance:** What is the tolerance for flaky tests? Is there a quarantine process?
- **Test execution time:** What is the target test execution time? (fast feedback for unit tests, slower for integration/E2E)

### If Any Dimension Applies

The work agreement must include:
- required test types
- coverage targets and enforcement mechanism
- test infrastructure plan
- test data strategy
- test environment definitions
- performance testing requirements (if any)
- contract testing requirements (if any)
- regression prevention strategy
- flaky test policy

Testing strategy is a discovery concern because it shapes the work itself — the tests are part of the deliverable, not an afterthought. See `23_TESTING_STRATEGY_PROTOCOL.md` for the full testing strategy protocol.

---

## Dimension Category 13 — Dependency Landscape

### When to Check
For any system that has external dependencies (libraries, frameworks, services, APIs) or will introduce new dependencies.

### Dimensions to Surface

- **Existing dependencies:** What dependencies does the system currently have? (runtime, build, test, dev)
- **Dependency versions:** What versions are in use? Are they pinned, floating, or ranged? Are they up to date?
- **Dependency licenses:** What are the licenses of each dependency? (MIT, Apache 2.0, GPL, LGPL, proprietary) Are there license compatibility issues?
- **Dependency security status:** Are there known vulnerabilities in any dependency? (CVEs, advisories) What is the severity?
- **Dependency maintenance:** Are dependencies actively maintained? Are they abandoned? Are there maintained forks?
- **New dependencies needed:** Does the work require new dependencies? What are they? Why are they needed? Are there alternatives?
- **Dependency transitivity:** What are the transitive dependencies? Are they auditable? Are there conflicts?
- **Dependency provenance:** Where do dependencies come from? (public registries, private registries, vendored) Is provenance verified? (SBOM, signed packages)
- **Dependency isolation:** Are dependencies isolated from each other? (dependency injection, module boundaries) What are the coupling risks?
- **Dependency removal:** Are there dependencies that should be removed? (unused, redundant, risky)

### If Any Dimension Applies

The work agreement must include:
- existing dependency inventory with versions and licenses
- dependency security status (known vulnerabilities)
- new dependencies to be introduced (with justification)
- dependency provenance and verification strategy
- transitive dependency audit
- dependency removal plan (if any)

Dependencies are a discovery concern because they introduce risk, licensing obligations, maintenance burdens, and security exposure — all of which must be understood before the work begins, not after. See `28_DEPENDENCY_MANAGEMENT_PROTOCOL.md` for the full dependency management protocol.

---

## Protocol Application Summary

| Dimension Category | When to Check | Depth |
|---|---|---|
| Safety and Criticality | Any system where failure has real-world consequences | Full in Stable, check in Formative, minimal in Exploratory |
| Compliance and Regulatory | Any system handling personal, financial, or health data | Full in Stable, check in Formative, minimal in Exploratory |
| Non-Functional Requirements | Any system with performance, scalability, or reliability targets | Full in Stable, check in Formative, check in Exploratory if viability depends on it |
| Hardware and Environmental | Embedded, IoT, mobile, edge computing | Full in Stable, check in Formative, check in Exploratory if viability depends on it |
| Machine Learning Specifics | Any system involving ML, AI models, or automated decisions | Full in Stable, check in Formative, check in Exploratory if viability depends on it |
| Large-Scale Migration | Any architecture migration | Full in Stable, full in Formative (migration shape matters), check in Exploratory |
| Large-Scale Legacy | Systems >100k LOC, >10 devs, >5 years, or heavy tech debt | Full in Stable, check in Formative, minimal in Exploratory |
| Multi-Team Coordination | Multiple teams or AI instances on same system | Full in Stable, full in Formative, check in Exploratory |
| Security and Threat Model | Any system with auth, sensitive data, or network exposure | Full in Stable, light check in Formative, skipped in Exploratory (unless viability depends on it) |
| Observability Requirements | Any system running in production | Full in Stable, light check in Formative, skipped in Exploratory (unless viability depends on it) |
| Data Governance Landscape | Any system that creates, reads, updates, or deletes data | Full in Stable, light check in Formative, skipped in Exploratory (unless viability depends on it) |
| Testing Strategy Requirements | Any production system requiring correctness verification | Full in Stable, light check in Formative, skipped in Exploratory (unless viability depends on it) |
| Dependency Landscape | Any system with external dependencies or new dependencies | Full in Stable, light check in Formative, skipped in Exploratory (unless viability depends on it) |

---

## Protocol Success Condition

The Discovery Dimension Protocol has been applied successfully when:

- every applicable dimension category has been checked during discovery
- applicable dimensions have been surfaced in the discovery output
- applicable dimensions have been incorporated into the work agreement
- non-applicable dimensions have been explicitly marked as "not applicable" (not silently skipped)
- the depth of dimension checking matches the operational state
- no dimension that materially affects the work is discovered after delivery

That is the official success condition of the Discovery Dimension Protocol.

---

## Next File

Continue to:

`23_TESTING_STRATEGY_PROTOCOL.md`
