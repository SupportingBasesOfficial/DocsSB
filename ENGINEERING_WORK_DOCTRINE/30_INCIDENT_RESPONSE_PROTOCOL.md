# INCIDENT RESPONSE PROTOCOL

## Purpose of This File

This file defines the official Incident Response Protocol of the Engineering Work Doctrine.

Its purpose is to govern what happens when work output causes an incident in production — how the incident is handled, how the root cause is found, and how corrective action prevents recurrence.

The doctrine governs how work is produced. But work is never finished when it ships. Production is the real test. When an incident occurs, the same doctrine that produced the work must govern how the incident is handled: how it is detected, how it is mitigated, how the root cause is found, and how corrective action prevents the same failure from happening again.

This is standard SRE practice at mega-tech companies. Incidents are inevitable. What separates a mature engineering organization from an immature one is not whether incidents happen, but how they are responded to: fast mitigation, blameless root-cause analysis, and corrective actions that close the gap that let the incident through.

This file defines:
- what severity levels exist and how they are classified
- what phases incident response moves through
- what a blameless post-mortem is and what it must contain
- the post-mortem template
- how incident response interacts with the doctrine's rules and states
- how the doctrine's existing mechanisms prevent incidents
- when the protocol has been applied successfully

> **Operational State Applicability:** Incident response applies to **Stable state** work only — incidents happen in production, and production is Stable. In Formative state, failures are expected and are handled through normal iteration, not incident response. In Exploratory state, failures are the method — throwaway work fails by design. This protocol activates when Stable work causes a production issue.

---

## Incident Severity Levels

Incident severity determines the urgency and scope of the response. Severity is assessed during triage and may be upgraded or downgraded as the incident evolves.

### SEV1 — Critical

System down, data loss, or security breach. The system is unavailable or compromised at a scope that affects the core function or the integrity of data.

- **Response:** Immediate. Page on-call. Open a war room.
- **Scope:** All hands available. Incident commander assigned immediately. Stakeholders notified within minutes.
- **Examples:** Production service fully down, database corruption, active security breach, payment processing failure affecting all users.

### SEV2 — High

Major functionality is broken, or there is significant user impact. The system is partially available, but a core flow that users depend on is failing.

- **Response:** Immediate. Page on-call.
- **Scope:** On-call leads response. Incident commander assigned. Stakeholders notified.
- **Examples:** Checkout broken for a region, authentication failing for a subset of users, critical API returning errors, degraded performance making the system unusable.

### SEV3 — Medium

Partial degradation with a workaround. The system is functioning, but a non-critical feature or flow is impaired, and users can work around the issue.

- **Response:** Within business hours.
- **Scope:** Assigned to the appropriate team. Tracked as an active incident, not a paged emergency.
- **Examples:** Non-critical feature unavailable, intermittent errors with retry success, slow performance below SLO but above unusable.

### SEV4 — Low

Minor issue with minimal impact. The system is functioning normally for the vast majority of users. The issue is real but does not affect core flows.

- **Response:** Ticket for later investigation.
- **Scope:** Filed as a bug or improvement ticket. No active incident response.
- **Examples:** Cosmetic defect in a non-critical surface, rare edge-case error, minor performance dip above SLO.

---

## Incident Response Phases

Every incident moves through the same phases. The depth of each phase scales with severity, but the phases themselves do not change.

### 1. Detect

The incident is identified. Detection comes from one of three sources:

- **Alert fires** — monitoring or an SLO-based alert catches the issue before users are affected (the goal of the Observability Protocol)
- **User reports** — users report the issue through support, forums, or direct contact
- **Monitoring catches it** — dashboards or anomaly detection surface a deviation from expected behavior

Detection is the first signal. The clock starts here.

### 2. Triage

The incident is assessed and organized. Triage determines:

- **Severity** — SEV1, SEV2, SEV3, or SEV4, based on impact and urgency
- **Incident commander** — the person who owns the response and coordinates the work
- **Stakeholder notification** — who needs to know, and when (internal teams, leadership, users)

Triage is fast. Severity can be revised as more is learned. The goal is to have someone in charge and the right people notified within minutes for SEV1/SEV2.

### 3. Mitigate

Stop the bleeding. The goal is not to fix the root cause — it is to reduce impact as fast as possible. Mitigation techniques include:

- **Rollback** — revert the deployment that introduced the issue (the Rigid Payload's Rollback section exists for this)
- **Feature flag off** — disable the feature that is causing the problem
- **Redirect traffic** — route users away from the failing component to a healthy one
- **Restart** — restart the affected service or component to clear a bad state
- **Scale out** — add capacity to absorb the load

Mitigation is temporary. It buys time for root cause resolution. An incident is mitigated when impact stops growing; it is resolved when the root cause is fixed.

### 4. Resolve

Fix the root cause. The fix follows the doctrine's Fix Path (`03_PROJECT_LIFECYCLE.md`): understand the root cause, plan the fix, execute, and verify. The fix must be held to the same quality bar as any other Stable work — tests, review, observability.

Resolution is complete when the root cause is fixed, the fix is deployed, the fix is verified in production, and the system is confirmed healthy.

### 5. Post-mortem

Blameless review of what happened, why, and how to prevent recurrence. The post-mortem is the learning artifact. It is mandatory for SEV1 and SEV2, recommended for SEV3. See the Blameless Post-Mortem section below.

### 6. Corrective Action

Implement preventive measures identified in the post-mortem. Corrective actions are specific, owned, and tracked to completion. They may include:

- **Tests** — add tests that would have caught the bug before it shipped
- **Alerts** — add alerts that would have detected the issue earlier
- **Runbooks** — document the response steps so the next responder does not rediscover them
- **Process changes** — change the process that allowed the issue through (review, deployment, configuration)

Corrective actions are not suggestions. They are work items. They enter the work backlog and are tracked under the same doctrine as any other work.

---

## Incident Response by Operational State

Incident response applies to **Stable state** work only — incidents happen in production, and production is Stable.

- **Exploratory state:** Not applicable. Failures are the method. Throwaway work fails by design.
- **Formative state:** Not applicable. Failures are expected and handled through normal iteration, not incident response.
- **Stable state:** Full protocol applies. When Stable work causes a production issue, the incident response protocol is activated.

---

## Blameless Post-Mortem

The post-mortem is the most important artifact of incident response. It is where the organization learns. A post-mortem that assigns blame teaches people to hide incidents. A post-mortem that focuses on the system teaches people to fix the system.

The post-mortem must be:

- **Blameless** — focus on the system, not the people. The question is "What failed?" not "Who failed?" People operate within the systems they are given. If a person made a mistake, the question is what system allowed that mistake to cause an incident — missing guardrail, missing test, missing review, missing alert. Blameless does not mean consequenceless; it means the consequence is a better system, not a punished person.
- **Comprehensive** — the post-mortem covers the full picture: timeline, root cause, contributing factors, impact, what went well, what went poorly. A post-mortem that skips any of these is incomplete.
- **Actionable** — every post-mortem produces specific corrective actions with owners and deadlines. A post-mortem with no corrective actions is a narrative, not a learning artifact.
- **Documented** — the post-mortem is stored in a known location, accessible to all. It is not buried in a chat thread or a private document. Future responders must be able to find and learn from it.

---

## Post-Mortem Template

Every post-mortem follows this template. The structure is fixed so that post-mortems are comparable across incidents and so that no critical section is omitted.

- **Incident ID** — unique identifier for the incident (e.g., `INC-2025-001`)
- **Date** — when the incident occurred (start time and end time)
- **Severity** — SEV1, SEV2, SEV3, or SEV4
- **Summary** — one-paragraph description of what happened and what was affected
- **Timeline** — chronological events: when the issue was detected, when triage happened, when mitigation was applied, when resolution was deployed, when the system was confirmed healthy. Each event has a timestamp and a description.
- **Root cause** — what actually caused the incident. Not the symptom, not the first thing that broke — the underlying cause that, if removed, would have prevented the incident.
- **Contributing factors** — what made the incident worse, harder to detect, or slower to resolve. Contributing factors did not cause the incident, but they increased its impact or duration.
- **Impact** — users affected, duration of impact, data loss (if any), revenue impact (if any), SLO violation (if any)
- **What went well** — what helped mitigate the incident quickly. These are the strengths to preserve.
- **What went poorly** — what slowed down the response or made the incident worse. These are the gaps to close.
- **Corrective actions** — specific actions with owners and deadlines. Each action is a work item that enters the backlog.
- **Lessons learned** — what to do differently next time. The distilled takeaways that should change behavior.

---

## Incident Response and the Doctrine

Incident response does not suspend the doctrine — it operates within it, with specific adjustments for speed.

- **Incident mitigation may use Process Override (Rule 14.2)** — during an active SEV1/SEV2 incident, speed is the priority. The incident commander may apply a Process Override to skip or accelerate doctrinal stages (e.g., skip discovery, skip full review) to mitigate faster. The override is recorded, and the work is brought back into full doctrinal compliance after mitigation. See `08_DECISION_RULES.md`, Rule 14.2.
- **Root cause resolution follows the Fix Path in Stable state** — once the incident is mitigated, the root cause fix is not an emergency. It follows the Fix Path (`03_PROJECT_LIFECYCLE.md`) with full doctrine: discovery of root cause, plan, execute, verify. The fix is held to 100% as Floor.
- **Corrective actions may spawn new work items** — the post-mortem's corrective actions (tests, alerts, runbooks, process changes) become work items. They are classified, prioritized, and tracked under the doctrine like any other work.
- **Post-mortem is mandatory for SEV1 and SEV2** — no SEV1 or SEV2 incident is closed without a blameless post-mortem with corrective actions. Post-mortem is recommended for SEV3 and optional for SEV4.

---

## Incident Prevention

The doctrine's existing mechanisms are the first line of incident prevention. Each protocol exists, in part, to keep incidents from happening in the first place:

- **100% as Floor prevents shipping broken code** — the doctrine's core rule (`01_DOCTRINE_FOUNDATION.md`) requires that work be 100% verified before it is declared complete. Work that is not verified does not ship. This is the primary barrier against incidents caused by unverified changes.
- **Security Review Protocol prevents security incidents** — `26_SECURITY_REVIEW_PROTOCOL.md` ensures that security-relevant changes are reviewed before shipping, closing the gaps that lead to security incidents.
- **Observability Protocol ensures incidents are detected quickly** — `25_OBSERVABILITY_PROTOCOL.md` ensures that the system produces the logs, metrics, traces, and alerts that catch incidents before users do. Fast detection is fast mitigation.
- **Testing Strategy Protocol ensures code is verified** — `23_TESTING_STRATEGY_PROTOCOL.md` defines what "100% verified" means concretely: the right test types for the work type and operational state. Verified code is code that is less likely to cause an incident.
- **The Rigid Payload's Rollback section ensures quick mitigation** — `20_ENFORCEMENT_LAYER.md` requires that every Stable implementation output include a Rollback plan. When an incident occurs, the rollback plan is already written. Mitigation is not improvisation; it is execution of a plan that was prepared before the incident.

Incident response is the last line of defense. The earlier protocols are the earlier lines. The doctrine's goal is not to respond to incidents well — it is to prevent them, and to respond well when prevention is not enough.

---

## Incident Response in the Rigid Payload

When implementation work is deployed to production (Stable state), the Rigid Payload's Enforcement section must include:
- **Rollback plan verification** — the rollback plan described in the Rollback section has been verified (tested or reviewed)
- **Incident response readiness** — the team knows how to respond to incidents involving this work (procedure documented, escalation path defined)
- **Monitoring confirmation** — the work is monitored by the appropriate alerts (see `25_OBSERVABILITY_PROTOCOL.md`)

This ensures that incident response is not an afterthought — it is prepared before the work reaches production.

---

## Incident Response Anti-Patterns

The following are incident response anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Blameful post-mortem** — a post-mortem that focuses on who caused the incident instead of why the system allowed it. Blameful post-mortems teach people to hide incidents.
- **No rollback plan** — deploying to production without a tested rollback plan. When the deployment fails, mitigation is improvisation.
- **No incident response procedure** — an incident occurs and no one knows what to do. No severity levels, no escalation path, no communication plan.
- **Fixing the symptom, not the root cause** — the incident is mitigated, but the root cause is not addressed. The same incident recurs.
- **No post-mortem for minor incidents** — only major incidents get post-mortems. Minor incidents are the early warnings; ignoring them means missing the pattern.
- **No monitoring for critical paths** — critical operations with no alerts. The team learns about incidents from users, not from the system.

---

## Incident Response and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that if the work is deployed to production, the rollback plan is verified and the incident response procedure is documented. No work enters Stable state without incident response readiness (if deployed).

---

## Protocol Success Condition

The Incident Response Protocol has been applied successfully when:

- every SEV1 and SEV2 incident has a blameless post-mortem with corrective actions
- every post-mortem follows the official template with all sections completed
- every corrective action has an owner and a deadline and is tracked to completion
- incident mitigation used Process Override where speed required it, with the override recorded
- root cause resolution followed the Fix Path with full doctrine applied
- no SEV1 or SEV2 incident is closed without a post-mortem
- corrective actions from past incidents are verifiably completed, not left open

That is the official success condition of the Incident Response Protocol.

Incident metrics — including MTTR (mean time to recovery) and change failure rate — feed into the DORA metrics tracked in `34_METRICS_FEEDBACK_LOOP.md`. See `34_METRICS_FEEDBACK_LOOP.md` for how these incident-derived metrics are used to measure and improve delivery performance over time.

**Anti-pattern:** See ANTI-PATTERN 38 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.9 in `08_DECISION_RULES.md`.

---

## Next File

`31_QUALITY_GATES.md`
