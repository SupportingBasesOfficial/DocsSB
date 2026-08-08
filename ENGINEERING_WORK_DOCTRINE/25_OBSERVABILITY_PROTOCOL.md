# OBSERVABILITY PROTOCOL

## Purpose of This File

This file defines the official Observability Protocol of the Engineering Work Doctrine.

In production, you cannot manage what you cannot see. The doctrine requires that work output in **Stable** state includes the observability needed to operate, debug, and monitor the system. This is standard SRE practice at mega-tech companies.

Observability is not an add-on. It is not a "we'll do it later." It is a delivery requirement, on equal footing with functionality, tests, and documentation. A system that works but cannot be observed is not ready for production.

This file defines what observability means, what is required for each work type and operational state, and the standards that logs, metrics, traces, alerts, and dashboards must meet.

---

## The Three Pillars of Observability

Observability rests on three pillars. A system is observable when all three are present and connected.

### 1. Logs

**Definition:** Discrete events with structured data.

A log is a record of something that happened at a point in time. Each log line must carry enough structured context to be queried, filtered, and correlated without reading free text.

Required fields:
- **timestamp** — when the event occurred (UTC, ISO 8601)
- **level** — severity of the event (DEBUG, INFO, WARN, ERROR, FATAL)
- **context** — what happened, where, and why
- **correlation ID** — the trace ID that links this log to the request flow it belongs to

### 2. Metrics

**Definition:** Numeric measurements over time.

A metric is a number that changes over time, collected at intervals or on events. Metrics are the foundation of dashboards, alerts, and trend analysis.

Types:
- **Counters** — values that only increase (e.g., total requests, total errors)
- **Gauges** — values that go up and down (e.g., active connections, queue depth)
- **Histograms** — distribution of values (e.g., request latency across percentiles)
- **Summaries** — precomputed percentiles (e.g., p50, p99 of request duration)

### 3. Traces

**Definition:** Request flow across services.

A trace is the end-to-end journey of a single request as it moves through the system. A trace is composed of spans, each representing a unit of work.

Required fields per span:
- **trace ID** — links all spans in the same request flow
- **span ID** — unique within the trace
- **service** — which service performed the work
- **operation** — what operation was performed
- **duration** — how long the operation took

---

## Observability Requirements by Work Type

Observability depth scales with work type, like all other doctrine requirements.

| Work Type | Observability Required |
|---|---|
| Project | Full observability — logs + metrics + traces + alerts + dashboards |
| Feature | Observability for the new feature — logs + metrics + alerts for the feature |
| Refactoring | Preserve existing observability; add if missing |
| Bugfix | Add observability that would have helped detect or diagnose the bug |
| Task | Minimal — logs if the task affects production behavior |
| Question | None |

### Project

A project delivers a new system or major subsystem. Full observability is required:
- structured logs with correlation IDs across all services
- metrics covering resources (USE), services (RED), and business domain
- distributed traces for all multi-service flows
- alerts based on SLOs with runbooks
- service-level, business-level, and incident dashboards

### Feature

A feature adds new capability to an existing system. Observability is required for the feature's surface area:
- logs for the new feature's operations
- metrics for the feature's rate, errors, and duration
- alerts for the feature's failure modes
- dashboard panels added to existing service dashboards

### Refactoring

A refactoring changes internal structure without changing behavior. Existing observability must be preserved. If the refactoring exposes a gap in observability (e.g., a service that had no metrics), that gap must be filled as part of the refactoring. You do not refactor a system into a less observable state.

### Bugfix

A bugfix resolves a defect. The bugfix must add the observability that would have helped detect or diagnose the bug earlier. If the bug was a latency spike, add latency metrics and an alert. If the bug was a data corruption, add integrity checks and logs. The question is: **what would have caught this before a user reported it?**

### Task

A task is a small, well-scoped change. If the task affects production behavior, logs are required. If it does not affect production behavior (e.g., documentation update), no observability is required.

### Question

A question produces an answer, not a code change. No observability is required.

---

## Observability Requirements by Operational State

Observability requirements scale with operational state, like all other doctrine requirements.

| Operational State | Observability Required |
|---|---|
| Exploratory | Not required — throwaway output |
| Formative | Logs recommended; metrics when committing |
| Stable | Full observability required — logs + metrics + traces + alerts + dashboards |

### Exploratory

Exploratory work is throwaway. Observability is not required. The goal is to learn whether something is viable, not to operate it.

### Formative

Formative work is actively being shaped. Logs are recommended so that behavior can be understood during development. When a formative change is committed (entering a more durable state), metrics should be added for the committed surface area.

### Stable

Stable work is production, live, and precious. Full observability is required and non-negotiable. A Stable work item that does not produce logs, metrics, and traces is not done.

---

## Log Standards

All logs in Stable state must meet these standards.

### Structured

Logs must be structured — JSON or key-value pairs, not free text. Free-text logs cannot be reliably queried, filtered, or correlated.

Good:
```json
{"timestamp":"2025-01-15T12:34:56Z","level":"ERROR","trace_id":"abc123","service":"orders","operation":"create_order","user_id":"u789","message":"payment gateway timeout","duration_ms":5000}
```

Bad:
```
[2025-01-15 12:34:56] ERROR: payment failed for some user, took too long
```

### Correlation IDs

Every log line in a request flow must share a trace ID. This is what allows an operator to reconstruct the full journey of a request across services by filtering on a single ID. Logs without correlation IDs are isolated events that cannot be traced back to their origin.

### Levels

| Level | When to Use |
|---|---|
| DEBUG | Detailed diagnostic information, disabled in production by default |
| INFO | General operational events — request received, job started, service initialized |
| WARN | Something unexpected happened, but the system is still functioning correctly |
| ERROR | A failure occurred — the operation could not be completed, but the system continues |
| FATAL | A critical failure — the system cannot continue and must terminate or fail over |

### No Sensitive Data

Logs must never contain:
- passwords
- tokens (API keys, session tokens, JWTs)
- PII (personally identifiable information) unless explicitly required and approved
- secrets of any kind

If sensitive data must be referenced, it must be redacted or replaced with a non-reversible identifier.

### Context-Rich

Every log line must answer: **what happened, where, why, and who.**
- **what** — the event or operation
- **where** — the service, module, function
- **why** — the trigger or cause (if known)
- **who** — the user, request, or system that initiated it

---

## Metric Standards

All metrics in Stable state must meet these standards.

### USE Method for Resources

For resources (CPU, memory, disk, network), use the **USE method**:
- **Utilization** — percentage of time the resource is busy
- **Saturation** — amount of work queued, waiting, or blocked
- **Errors** — count of errors encountered

### RED Method for Services

For services (APIs, endpoints, handlers), use the **RED method**:
- **Rate** — number of requests per unit of time
- **Errors** — number of failed requests per unit of time
- **Duration** — distribution of request latency (histogram or summary)

### Business Metrics for Domain

For the business domain, define metrics that capture domain behavior:
- orders placed, orders completed, orders failed
- users signed up, users active, users churned
- conversions started, conversions completed, conversion rate

Business metrics connect technical observability to business outcomes. They are what stakeholders care about.

### Naming Convention

Metrics must follow a consistent naming convention: `namespace_metric_submetric`

Examples:
- `http_requests_total` — total HTTP requests (counter)
- `http_request_duration_p99` — p99 latency of HTTP requests (summary)
- `orders_created_total` — total orders created (counter)
- `db_connections_active` — active database connections (gauge)

The namespace groups related metrics. The submetric distinguishes variants (e.g., percentiles, status codes).

---

## Trace Standards

All traces in Stable state must meet these standards.

### Distributed Tracing for Multi-Service Flows

Any flow that crosses a service boundary must be traced end-to-end. A request that enters the API gateway, calls the orders service, which calls the payment service, which calls the database — all of that must appear as a single trace with spans for each hop.

### Span per Significant Operation

Each significant operation gets its own span. "Significant" means: a network call, a database query, a non-trivial computation, or a business operation. Trivial operations (in-memory variable assignment) do not get spans.

### Context Propagation Across Service Boundaries

The trace ID and span context must be propagated across service boundaries — typically via headers (e.g., `traceparent`, `tracestate` in W3C Trace Context). A service that receives a request without a trace ID must start a new trace; a service that receives a request with a trace ID must continue it.

### Sampling Strategy

Not every request must be traced — tracing has overhead. But **every error must be traced**. A typical strategy:
- sample a small percentage of successful requests (e.g., 1-10%)
- trace 100% of failed requests (errors, exceptions, timeouts)
- trace 100% of slow requests (above a latency threshold)

This ensures that the interesting requests — the ones that went wrong — are always available for diagnosis.

---

## Alert Standards

All alerts in Stable state must meet these standards.

### Alert on Symptoms, Not Causes

Alert on **user impact**, not internal state. A symptom is "users are seeing errors." A cause is "the cache hit rate dropped." Alert on the symptom; investigate the cause during the response.

Bad alert: "cache hit rate below 80%"
Good alert: "error rate for checkout API above 1% for 5 minutes"

### Alert Thresholds Based on SLOs

Alert thresholds must be derived from SLOs, specifically from **error budget burn rate**. If the SLO is 99.9% availability, the error budget is 0.1%. Alerts should fire when the burn rate threatens to exhaust the budget within a meaningful window (e.g., burning 2% of the monthly budget in 1 hour).

### Alert Severity

| Severity | Meaning | Response |
|---|---|---|
| Page | User impact is happening now | Wake someone up — immediate response required |
| Ticket | Something needs investigation | Investigate when convenient — within working hours |
| Info | Notable but not actionable | Dashboard only — no notification |

### No Alert Storms

Alert storms — dozens of alerts firing at once for the same underlying issue — are a failure of alert design. Prevent them by:
- **grouping** — related alerts roll up into a single notification
- **suppression** — if a higher-severity alert is firing, suppress the lower-severity ones for the same subsystem
- **correlation** — alerts that share a common cause should be linked

### Every Alert Must Have a Runbook

Every alert must link to a runbook that tells the responder:
- what the alert means
- how to confirm the issue is real
- what to check first
- what the likely causes are
- how to mitigate or resolve
- when to escalate

An alert without a runbook is noise. The responder does not know what to do, and the alert becomes a source of panic rather than a source of signal.

---

## Dashboard Standards

All dashboards in Stable state must meet these standards.

### Service-Level Dashboards

Every service must have a dashboard showing:
- **health** — is the service up? (uptime, readiness)
- **traffic** — how much load is it handling? (request rate)
- **errors** — how many requests are failing? (error rate)
- **latency** — how fast is it responding? (p50, p95, p99)

This is the RED method visualized. It is the first dashboard an operator looks at during an incident.

### Business-Level Dashboards

The system must have dashboards showing key business metrics:
- key metrics (orders, users, revenue)
- funnels (conversion from one stage to the next)
- conversions (rate and absolute numbers)

These dashboards connect technical health to business outcomes. They are what stakeholders look at.

### Incident Dashboards

The system must have a dashboard designed specifically for incident response — what to look at during an incident:
- error rates across all services
- latency across all services
- recent deployments and changes
- active alerts
- error budget status

This dashboard exists so that during an incident, the responder does not waste time assembling views. It is pre-built and ready.

---

## Observability in the Rigid Payload

The Rigid Payload (defined in `20_ENFORCEMENT_LAYER.md`) has four sections: Diagnóstico, Alterações, Enforcement, Rollback. Observability touches two sections:

- **Alterações** — what observability was added or modified (logs, metrics, traces, alerts, dashboards). This is a record of what changed, like any other code change.
- **Enforcement** — how observability was verified (e.g., "logs verified in staging," "metrics confirmed in dashboard," "alert tested by triggering condition").

The Alterações section must include:
- **logs added or modified** — what log events were added, changed, or removed
- **metrics added or modified** — what metrics were added, changed, or removed
- **traces added or modified** — what trace spans or sampling rules were added, changed, or removed
- **alerts added or modified** — what alerts were added, changed, or removed (with runbook links)
- **dashboards added or modified** — what dashboards were added, changed, or removed

If a work type does not require observability (e.g., Question), the Alterações section must state: "No observability changes — work type does not require observability."

This ensures that observability is not silently skipped. It must be explicitly accounted for in every work item's delivery record.

---

## Observability Anti-Patterns

The following are observability anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Observability as afterthought** — observability is added after deployment, when something breaks. In Stable state, observability is designed with the feature, not bolted on after.
- **Logs without structure** — free-text logs that cannot be parsed, searched, or aggregated. Logs in Stable state must be structured (JSON or key-value) with consistent fields.
- **Metrics without labels** — metrics that don't distinguish between endpoints, users, or error types. A single "request_count" metric is useless without labels.
- **No alerts on critical paths** — critical operations (payment, authentication, data write) with no alerts. The team learns about failures from users, not from the system.
- **Alert fatigue** — too many alerts, most of them non-actionable. The team ignores alerts because most are noise. When a real alert fires, it is missed.
- **No tracing for distributed calls** — a request that spans multiple services with no trace. When latency spikes, the team cannot identify which service is slow.
- **Dashboards that show everything** — dashboards with 50 panels that no one can read. A dashboard should answer a specific question; if it can't, it's decoration.

---

## Observability and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that observability infrastructure (logs, metrics, traces, alerts, dashboards) is present for the stabilized surface area. No work enters Stable state without being observable.

---

## Protocol Success Condition

The Observability Protocol has been applied successfully when:

- every Stable work item produces logs, metrics, and traces that allow operators to understand system behavior
- operators can detect problems before users report them
- operators can diagnose root causes from the observability data alone, without needing to reproduce the issue
- logs are structured, correlated, and free of sensitive data
- metrics follow USE, RED, and business conventions with consistent naming
- traces cover multi-service flows with context propagation and error sampling
- alerts fire on symptoms, are based on SLOs, do not storm, and have runbooks
- dashboards exist at service, business, and incident levels
- the Rigid Payload's Alterações section accounts for all observability changes

That is the official success condition of the Observability Protocol.

Observability is the foundation of incident detection — without logs, metrics, and alerts, incidents cannot be detected automatically. See `30_INCIDENT_RESPONSE_PROTOCOL.md` for how observability data drives the Detect phase of incident response.

**Anti-pattern:** See ANTI-PATTERN 33 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.4 in `08_DECISION_RULES.md`.

---

## Next File

`26_SECURITY_REVIEW_PROTOCOL.md`
