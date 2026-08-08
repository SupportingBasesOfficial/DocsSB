# DATA GOVERNANCE PROTOCOL

## Purpose of This File

Data is the most valuable and most regulated asset in modern systems. The doctrine surfaces compliance requirements during discovery (Discovery Dimension Protocol Category 2 — see `22_DISCOVERY_DIMENSION_PROTOCOL.md`), but work output must also govern how data is classified, stored, accessed, retained, and protected. A system that handles data without governance is a liability — data leaks, regulatory fines, and loss of trust are not bugs to be fixed later, they are failures of engineering discipline.

This is standard practice at mega-tech companies. Data is classified by sensitivity, encrypted at rest and in transit, access-controlled by role and need-to-know, retained per policy and regulation, and disposed of securely. The doctrine adopts the same standard.

This file defines the data governance protocol of the Engineering Work Doctrine: how data is classified, how each classification is handled, how access is controlled, how retention and disposal are governed, how data migrations are made safe, how data governance is recorded in the Rigid Payload, how governance scales with the Operational State, and when the protocol has been applied successfully.

---

## Data Classification Levels

All data in the system must be classified into one of the following levels. Classification is the foundation of governance — you cannot protect what you have not classified.

1. **Public** — data that can be freely shared without harm. This includes documentation, public profiles, marketing content, and any data explicitly intended for public consumption. Public data still has integrity requirements (it must not be tampered with), but no confidentiality requirements.

2. **Internal** — data for internal use only. This includes internal documentation, employee directories, internal metrics, and operational data that is not business-sensitive but is not for external consumption. Internal data exposed publicly is an embarrassment, not a catastrophe.

3. **Confidential** — business-sensitive data. This includes financial data, business plans, source code, strategic roadmaps, and any data whose exposure would harm the business. Confidential data exposed externally is a material incident.

4. **Restricted** — highly sensitive data. This includes personally identifiable information (PII), protected health information (PHI), payment data, credentials, secrets, and any data whose exposure would harm individuals or trigger regulatory consequences. Restricted data exposed externally is a critical incident with legal and regulatory impact.

---

## Data Handling by Classification

Each classification level has mandatory handling requirements. The requirements scale with sensitivity — more sensitive data requires stronger protection.

| Level | Encryption at Rest | Encryption in Transit | Access Control | Logging | Retention |
|---|---|---|---|---|---|
| Public | Optional | Optional | None | Minimal | Unlimited |
| Internal | Recommended | Required | Role-based | Standard | Per policy |
| Confidential | Required | Required | Role-based + MFA | Detailed | Per policy |
| Restricted | Required (strong) | Required (strong) | Need-to-know + MFA + audit | Full audit trail | Per regulation |

These are the minimum requirements. A work item may exceed them — it may never fall below them. A Restricted dataset stored without strong encryption at rest is a defect, not a configuration choice.

---

## Data Access Principles

Access to data is governed by the following principles. These principles apply to all data, but their enforcement is strictest for Confidential and Restricted data.

- **Least privilege** — access only what you need. A user, service, or component is granted the minimum access required to perform its function. Broad access "for convenience" is a defect. Privilege is granted by default-deny, not default-allow.
- **Need-to-know** — access only data relevant to your role. Even if a user has the technical permission to access data, they should only access data that is relevant to their current work. Need-to-know is a human discipline enforced by access segmentation.
- **Audit trail** — all access to Confidential and Restricted data is logged. The log records who accessed what, when, from where, and for what purpose. An audit trail that is not reviewed is a partial control — logs must be monitored for anomalous access patterns.
- **Access review** — access rights are reviewed periodically. Access that was once needed but is no longer needed is revoked. Access reviews are scheduled, not ad-hoc — quarterly for Restricted, semi-annual for Confidential, annual for Internal.
- **No shared credentials** — each user and each service has its own identity. Shared credentials make audit trails useless (you cannot attribute access to an actor) and make revocation impossible (you cannot revoke one user's access without affecting others). Every service account is a distinct identity with distinct credentials.

---

## Data Retention and Disposal

Data is not kept forever by default. Retention and disposal are governed explicitly.

- **Retention policies defined per data type and classification** — every data type has a defined retention period, based on its classification and business need. Data without a retention policy is data that accumulates forever, which is a storage cost, a security risk, and a regulatory liability.
- **Regulatory minimums respected** — where regulation mandates a minimum retention period, that minimum is the floor. Financial records are retained for 7 years (common regulatory standard). Medical records are retained per HIPAA or equivalent. The retention policy may exceed the regulatory minimum but may never fall below it.
- **Right to be forgotten supported where required** — where GDPR or equivalent regulation grants individuals the right to request deletion of their personal data, the system must support that right. This includes deletion from primary stores, backups, logs, and derived datasets. A right-to-be-forgotten request that only deletes from the primary database is not compliance.
- **Data disposal is secure** — deletion is not disposal. Secure disposal means the data cannot be recovered: secure wipe (overwriting storage), crypto-shredding (destroying the encryption key so the ciphertext becomes unrecoverable), or physical destruction of media. A `DELETE` that leaves data recoverable on disk is not secure disposal.
- **Backups have their own retention schedule** — backups are not exempt from retention policy. A backup that retains Restricted data indefinitely is a retention violation. Backup retention is defined separately from primary data retention, and must account for the time window during which deleted data remains recoverable from backup.

---

## Data Migration Safety

Data migrations — schema changes, data format changes, store changes, platform moves — are high-risk operations. A failed migration can corrupt data, lose data, or make the system unavailable. The doctrine governs migrations explicitly.

- **Backward-compatible** — data migrations are backward-compatible. The old version of the system must continue to work during and after the migration. This is the Zero-Downtime principle defined in `20_ENFORCEMENT_LAYER.md`. A migration that requires downtime is a last resort, not a default.
- **Data integrity verified after migration** — after migration, integrity is verified: checksums match, row counts match, referential integrity holds. A migration that reports success without verifying integrity is an unverified migration — it may have silently lost or corrupted data.
- **Migration is reversible** — there is a rollback path. If the migration fails or produces unexpected results, the system can be returned to its pre-migration state. A migration without a rollback path is a one-way door — and one-way doors are prohibited in Stable state without explicit executive approval.
- **Sensitive data is encrypted during migration** — data in transit during migration is encrypted. Restricted and Confidential data is encrypted at rest in the migration staging area. A migration that moves Restricted data over an unencrypted channel is a data exposure incident.
- **Migration is tested in staging before production** — the migration is run against a staging dataset that mirrors production in structure and scale. A migration that runs for the first time in production is a gamble, not an engineering practice.

---

## Data and the Rigid Payload

If a work item touches data — schema changes, storage changes, access changes, retention changes — the Rigid Payload must state the data governance implications explicitly. The Alterações section must include a data record that states:

- **What data classification level is affected** — which classifications does this work item touch (Public, Internal, Confidential, Restricted)? A work item that touches Restricted data has different obligations than one that touches Public data.
- **How data is protected** — what encryption (at rest, in transit), what access control (role-based, need-to-know, MFA) is applied. A work item that touches data but does not state its protection is a work item with an incomplete security posture.
- **What access patterns are introduced or changed** — what new access paths does this work item create? What existing access paths does it modify? Access patterns are the surface area of data — every new path is a new potential exposure.
- **What retention policy applies** — what is the retention period for the data touched by this work item? Is it defined, or is it inheriting a default? Data without an explicit retention policy is data with an implicit "forever" policy, which is a defect.
- **What compliance requirements apply** — what regulatory or contractual requirements govern this data? This references the Discovery Dimension Protocol Category 2 (see `22_DISCOVERY_DIMENSION_PROTOCOL.md`), where compliance requirements are surfaced during discovery. A work item that touches regulated data without referencing the applicable compliance requirements is a work item that has not completed discovery.

A Rigid Payload that touches data but omits the data record is incomplete. The work cannot be declared 100% complete.

---

## Data Governance by Operational State

Data governance scales with the Operational State, like all doctrine protocols.

1. **Exploratory** — No governance. Exploratory work uses throwaway data — sample datasets, mock data, synthetic data. Classifying and governing throwaway data is ceremony that kills exploration. If the exploration touches real production data, it is not Exploratory — it is Stable, and full governance applies.

2. **Formative** — Classification when the data model is frozen; protection when committing. During active development, the data model is still evolving, and classification may be premature. But once the data model is frozen — once the structure of the data is stable enough to describe — classification is required. Protection (encryption, access control) is required when code is committed, not when it is deployed. The bar is "data is classified and protected before it leaves the developer's machine," not "data is governed when it reaches production."

3. **Stable** — Full data governance required. Every data element is classified, protected, access-controlled, retained per policy, and audited according to its classification level. There are no unclassified data stores, no unencrypted Restricted data, no access without audit trail. Full governance is non-negotiable in Stable state.

This scaling prevents two failure modes:

1. Requiring governance in Exploratory — kills exploration with ceremony
2. Not requiring governance in Stable — leaves data unprotected when it matters most

---

## Data Governance and the Consolidation Moment

The Consolidation Moment (defined in `21_OPERATIONAL_STATES.md`, protocol in `05_CONSOLIDATION_PROTOCOL.md`) is the gate before work enters Stable state. Data governance is part of that gate. The Consolidation Moment must include:

- **Data classification review** — all data touched by the work is classified. No unclassified data enters Stable state. If a data element cannot be classified, the work is not ready for consolidation.
- **Access control review** — least privilege is verified. Every access path is examined: does it grant more than needed? Is access default-deny? Are there shared credentials? Access that is overly permissive is corrected before consolidation.
- **Retention policy defined** — every data type has a retention period. Data without a retention policy does not enter Stable state — it is assigned one first.
- **Encryption verified** — encryption at rest and in transit is confirmed for all Confidential and Restricted data. A configuration that claims encryption but has not been verified is an assumption, not a fact.
- **Audit trail confirmed** — for all Confidential and Restricted data, the audit trail is confirmed to be capturing who, what, when, where, and why. An audit trail that is not tested is a control that may fail silently.

A work item that reaches the Consolidation Moment without completing the data governance review is not ready for Stable state. The Consolidation Moment is a gate, not a rubber stamp.

---

## Data Anti-Patterns

The following are doctrinal anti-patterns. They must be rejected in review and corrected in Stable state.

- **Storing secrets in the database without encryption** — secrets (API keys, passwords, tokens) stored in plaintext in a database are a critical vulnerability. Secrets belong in a secrets manager (Vault, AWS Secrets Manager, etc.), not in a database column. A database is not a secrets store.
- **Logging sensitive data** — logging PII, PHI, payment data, credentials, or secrets is a data exposure incident waiting to happen. Logs are often less protected than databases, more widely accessible, and retained longer. Sensitive data in logs is sensitive data exposed.
- **Overly permissive access** — granting admin or broad access "for convenience" or "to avoid permission issues" is a defect. Overly permissive access defeats the purpose of access control and expands the blast radius of any credential compromise.
- **No retention policy** — data that accumulates forever is a storage cost, a security risk, and a regulatory liability. "We keep everything" is not a retention policy — it is the absence of one.
- **No audit trail for sensitive data access** — Confidential and Restricted data accessed without an audit trail is data that cannot be investigated. When a breach is suspected, the first question is "who accessed what?" — if there is no audit trail, the answer is "we don't know," which is itself a compliance violation.
- **Mixing data classification levels in the same store without segregation** — storing Public data alongside Restricted data in the same database, same table, or same bucket without segregation means the entire store must be treated as Restricted. This inflates the protection cost and expands the blast radius. Different classifications require different stores, or explicit segregation within a store.

---

## Protocol Success Condition

The data governance protocol has been applied successfully when:

1. All data in Stable state is classified into one of the four classification levels (Public, Internal, Confidential, Restricted).
2. All data is protected according to its classification level — encryption at rest and in transit, access control, logging — as defined in the handling table.
3. All access to Confidential and Restricted data is access-controlled (least privilege, need-to-know, MFA) and audited with a full audit trail.
4. All data has a defined retention policy that respects regulatory minimums, and disposal is secure.
5. All data migrations are backward-compatible, integrity-verified, reversible, encrypted, and tested in staging.
6. All work items that touch data include a data record in the Rigid Payload stating classification, protection, access patterns, retention, and compliance requirements.
7. The Consolidation Moment includes a data governance review before work enters Stable state.

That is the official success condition of the data governance protocol.

Data protection measures — encryption, access control, and audit trail integrity — are verified during security review per `26_SECURITY_REVIEW_PROTOCOL.md`. See `26_SECURITY_REVIEW_PROTOCOL.md` for the security review levels that apply to work touching data at each classification level.

**Anti-pattern:** See ANTI-PATTERN 41 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.12 in `08_DECISION_RULES.md`.

---

## Next File

The next file in the doctrine is `34_METRICS_FEEDBACK_LOOP.md`.
