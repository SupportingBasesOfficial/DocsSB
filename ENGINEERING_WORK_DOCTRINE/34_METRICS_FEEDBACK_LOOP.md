# METRICS & FEEDBACK LOOP PROTOCOL

## Purpose of This File

This file defines the official Metrics & Feedback Loop Protocol of the Engineering Work Doctrine.

Without measuring outcomes, the doctrine cannot know if it improves engineering results. A doctrine that governs work but does not measure the results of that governance is a doctrine operating on faith. Mega-tech companies measure everything: defect rate, time-to-fix, change failure rate, deployment frequency, MTTR. The doctrine adopts the same standard.

This file defines the metrics that the doctrine should track to evaluate its own effectiveness, how those metrics are collected, how they feed back into doctrine evolution, and when the protocol has been applied successfully.

---

## DORA Metrics

The four key metrics used by mega-tech (from the DORA / Accelerate research). These are the industry-standard metrics for measuring engineering delivery performance.

| Metric | What It Measures | Target |
|---|---|---|
| **Deployment Frequency** | How often work is delivered to production | High (daily or better for Stable) |
| **Lead Time for Changes** | Time from work start to delivery | Low (hours for small, days for medium) |
| **Change Failure Rate** | Percentage of changes that cause incidents | Low (<15%) |
| **Mean Time to Recovery (MTTR)** | Time from incident detection to resolution | Low (<1 hour for SEV1) |

These metrics are collected from version control (deployment frequency, lead time) and incident post-mortems (change failure rate, MTTR). They measure the delivery pipeline's health, not individual work items.

---

## Doctrine-Specific Metrics

In addition to DORA metrics, the doctrine tracks its own effectiveness. These metrics measure whether the doctrine's mechanisms are working as intended.

| Metric | What It Measures | Target |
|---|---|---|
| **Classification Accuracy** | How often the initial work type classification was correct (not re-classified mid-work) | High (>90%) |
| **State Accuracy** | How often the initial operational state was correct (not re-declared mid-work) | High (>90%) |
| **Discovery Completeness** | How often discovery surfaced all applicable dimensions (no late-discovered dimensions) | High (>95%) |
| **First Execution Success** | How often the first execution was correct (no rework needed) | High for Stable (>95%); variable for Formative |
| **Rigid Payload Compliance** | How often implementation work included the Rigid Payload | 100% for Stable |
| **Gate Pass Rate** | How often quality gates were passed on first attempt | High (>90%) |
| **Consolidation Moment Completion** | How often the Consolidation Moment was fully completed before entering Stable | 100% |
| **Post-Mortem Action Closure** | How often post-mortem corrective actions were completed | High (>90%) |
| **Technical Debt Payoff Rate** | How often scheduled debt was paid off on time | High (>80%) |

These metrics are the doctrine's self-assessment. If classification accuracy is below 90%, the classification guide (file 11) needs refinement. If discovery completeness is below 95%, the Discovery Dimension Protocol (file 22) needs strengthening. If gate pass rate is below 90%, the quality gates (file 31) may be too strict or the work is being rushed.

---

## Metrics Collection

Metrics should be collected from the following sources:

- **Work State Files** — classification, state, gate pass/fail (see `13_PROJECT_SESSION_TEMPLATE.md`)
- **Rigid Payloads** — first execution success, payload compliance (see `20_ENFORCEMENT_LAYER.md`)
- **Quality Gates** — gate pass rate, override frequency (see `31_QUALITY_GATES.md`)
- **Incident post-mortems** — change failure rate, MTTR (see `30_INCIDENT_RESPONSE_PROTOCOL.md`)
- **Debt Register** — debt payoff rate (see `27_TECHNICAL_DEBT_PROTOCOL.md`)
- **Version control** — deployment frequency, lead time

Metrics collection is not a separate activity. It is embedded in the artifacts the doctrine already produces. The Work State File, Rigid Payload, post-mortem, and Debt Register are the data sources — metrics are derived from them.

---

## Feedback Loop

Metrics are useless without a feedback loop. The doctrine's feedback loop is a four-step cycle:

1. **Measure** — collect metrics for each work item and each project. Metrics are recorded in the Work State File at work item completion.

2. **Analyze** — identify patterns. Which work types have lowest first-execution success? Which dimensions are most often missed in discovery? Which gates are most often overridden? Patterns reveal where the doctrine is working and where it is not.

3. **Adjust** — update the doctrine based on findings. Add rules, refine protocols, adjust thresholds. Doctrine adjustments are recorded in the Evolution Log (`18_EVOLUTION_LOG.md`) as new entries with the reason for the adjustment.

4. **Re-measure** — verify that the adjustment improved the metric. An adjustment that does not improve the metric is reverted or revised. The feedback loop is not complete until the re-measurement confirms the improvement.

This cycle ensures the doctrine evolves based on evidence, not opinion.

---

## Metrics Review Cadence

Metrics are reviewed at three levels:

- **Per work item** — record metrics in Work State File at completion. This is the atomic unit of measurement.
- **Per project** — aggregate metrics at project milestones. This reveals project-level patterns.
- **Per quarter** — review doctrine effectiveness and adjust. This is the strategic review that drives doctrine evolution.

The quarterly review is the point at which doctrine adjustments are considered. Individual work items and projects generate data; the quarterly review turns data into doctrine evolution.

---

## Metrics and Operational State

The metrics protocol scales with the Operational State, like all doctrine protocols:

- **Exploratory** — no metrics collected. Exploratory work is throwaway. Measuring throwaway work is ceremony that kills exploration.
- **Formative** — metrics are recorded but not gated upon. The work is still taking shape, and metrics may be noisy. Recording prepares for future analysis without imposing premature standards.
- **Stable** — metrics are recorded and used for continuous improvement. Stable work is where the doctrine's effectiveness is measured. Metrics drive doctrine evolution.

---

## Metrics and the Evolution Log

Significant metric findings should be recorded in the Evolution Log (`18_EVOLUTION_LOG.md`) as observations that inform future doctrine versions. A metric finding is significant when:

- it reveals a systemic issue (e.g., discovery completeness below 80% across multiple projects)
- it contradicts a doctrine assumption (e.g., classification accuracy is high but first-execution success is low, suggesting the classification is correct but the execution is flawed)
- it identifies a new pattern (e.g., a specific work type consistently has low gate pass rate)

Metric findings that are not significant (e.g., a single work item with low first-execution success) are recorded in the Work State File but do not warrant an Evolution Log entry.

---

## Metrics in the Rigid Payload

When implementation work is in Stable state, the Rigid Payload's Enforcement section must include:
- **Success metrics defined** — the metrics that determine whether the work is successful are defined (e.g., error rate, latency, adoption)
- **Collection mechanisms in place** — the instrumentation or collection method for each metric is confirmed
- **Baseline established** — where applicable, a pre-change baseline is recorded for comparison

This ensures that the work's success is measurable, not assumed.

---

## Metrics Anti-Patterns

The following are metrics anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Vanity metrics** — metrics that look good but don't inform decisions. "Total users" without "active users." "Total requests" without "error rate." Vanity metrics measure ego, not effectiveness.
- **No baseline** — metrics are collected but never compared to a baseline. The team doesn't know if the number is good, bad, or changing. A metric without a baseline is a number, not a measurement.
- **Metrics without action** — metrics are collected, dashboards are built, but no one acts on them. The metrics exist for show, not for decision-making.
- **Too many metrics** — tracking 100 metrics, none of them well-defined. The team is overwhelmed by data and cannot identify what matters. Focus on the few metrics that drive decisions.
- **No feedback loop** — metrics are collected but not reviewed. No cadence, no retrospective, no action items. The metrics are a museum exhibit, not a feedback loop.
- **Gaming the metrics** — optimizing for the metric instead of for the outcome. "Reduce MTTR" becomes "redefine incidents as non-incidents." The metric improves; the system doesn't.

---

## Metrics and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that success metrics are defined and collection mechanisms are in place (DORA metrics, doctrine compliance metrics). No work enters Stable state without defined success metrics and collection mechanisms.

---

## Protocol Success Condition

The metrics & feedback loop protocol has been applied successfully when:

1. Metrics are collected for every Stable work item, recorded in the Work State File.
2. Metrics are aggregated at project milestones and reviewed quarterly.
3. Doctrine adjustments are made based on metric findings, not opinion.
4. Adjustments are re-measured to confirm improvement.
5. The feedback loop is complete — measure, analyze, adjust, re-measure — not just the first step.

That is the official success condition of the Metrics & Feedback Loop Protocol.

**Anti-pattern:** See ANTI-PATTERN 42 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.13 in `08_DECISION_RULES.md`.

---

## Next File

→ `00_START_HERE.md` (this is the final file in the doctrine)
