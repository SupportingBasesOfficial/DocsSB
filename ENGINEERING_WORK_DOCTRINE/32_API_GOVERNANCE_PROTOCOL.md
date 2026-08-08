# API GOVERNANCE PROTOCOL

## Purpose of This File

APIs are the contracts between systems. Without governance, APIs become inconsistent, hard to use, and hard to maintain. Mega-tech companies have explicit API governance for naming, versioning, error handling, and consistency.

This file defines the API governance protocol of the Engineering Work Doctrine: the conventions, rules, and review process that govern how APIs are designed, documented, and evolved across the system's lifecycle.

---

## API Design Principles

All APIs in the doctrine must obey the following design principles:

1. **Consistency** — APIs within a system follow the same conventions. A consumer who learns one endpoint should be able to predict the rest.

2. **Predictability** — consumers can guess how an API behaves without reading docs. Conventions are strong enough that behavior is inferable from structure.

3. **Explicitness** — behavior is explicit, not implicit. No hidden side effects, no magic defaults that change based on context, no undocumented behavior.

4. **Versioning** — breaking changes are versioned, not silent. A consumer who upgrades a version should never have their integration break without warning.

5. **Documentation** — every API is documented (see `29_DOCUMENTATION_PROTOCOL.md`). An undocumented API is not a stable API — it is a private implementation detail exposed by accident.

6. **Contract-first** — the contract is defined before implementation. The API contract is the source of truth; the implementation conforms to the contract, not the reverse.

---

## Naming Conventions

API naming must follow these rules:

1. **Resources are nouns, not verbs** — `/users`, not `/getUsers`. The HTTP method expresses the verb; the URL expresses the resource.

2. **Actions are POST to a sub-resource** — `/users/123/activate`, not `/activateUser?id=123`. When an operation cannot be mapped to a standard CRUD verb, it becomes a named sub-resource.

3. **Plural for collections, singular for single resource** — `/users` for the collection, `/users/123` for a single resource.

4. **lowercase with hyphens for multi-word** — `/user-profiles`, not `/userProfiles` or `/user_profiles`. Hyphens are the URL standard; consistency within URLs is mandatory.

5. **Consistent field naming** — pick one convention (camelCase or snake_case) and stick to it across the entire API. Mixing conventions within a single API is a governance violation.

---

## Versioning Strategy

API versioning must follow these rules:

1. **URI versioning** (`/v1/users`) **or header versioning** (`Accept: application/vnd.api+json; version=1`) — both are valid approaches.

2. **Pick one and be consistent** — the system uses one versioning strategy across all endpoints. Mixing URI and header versioning is a governance violation.

3. **Breaking changes require a new version** — any change that could break an existing consumer (removing a field, changing a field type, changing behavior) must be released under a new version.

4. **Non-breaking changes do not require a new version** — adding optional fields, adding new endpoints, adding new response fields are all non-breaking and can be added to the current version.

5. **Old versions must be maintained during the deprecation period** — when a new version is released, the old version is not immediately removed. It is maintained until the deprecation period expires (see Deprecation Protocol in `07_DELIVERY_PROTOCOL.md`).

---

## Error Handling

Error handling must follow these rules:

1. **Consistent error response format** — all errors use the same structure:

   ```json
   {
     "error": {
       "code": "...",
       "message": "...",
       "details": { ... }
     }
   }
   ```

2. **HTTP status codes used correctly** — 2xx for success, 4xx for client error, 5xx for server error. A 200 with an error body is a governance violation.

3. **Error codes are machine-readable and consistent** — error codes are stable identifiers that consumers can branch on. They are not free-form text.

4. **Error messages are human-readable and do not leak internals** — the message explains what went wrong for a human, without exposing stack traces, internal paths, or implementation details.

5. **Validation errors include field-level details** — when a request fails validation, the error response identifies which fields failed and why:

   ```json
   {
     "error": {
       "code": "VALIDATION_FAILED",
       "message": "Request validation failed",
       "details": {
         "fields": [
           { "field": "email", "issue": "must be a valid email address" },
           { "field": "age", "issue": "must be a positive integer" }
         ]
       }
     }
   }
   ```

---

## Pagination

Pagination must follow these rules:

1. **Cursor-based pagination preferred** — for large datasets, cursor-based pagination is preferred over offset/limit. Offset/limit degrades in performance as the offset grows and produces inconsistent results when data changes between requests.

2. **Consistent pagination parameters** — use `cursor` and `limit`, or `before`, `after`, and `limit`. Pick one set and use it consistently across all paginated endpoints.

3. **Pagination response includes metadata** — the response must tell the consumer whether more data exists and how to get it:

   ```json
   {
     "data": [ ... ],
     "next_cursor": "abc123",
     "has_more": true
   }
   ```

   `total` may be included when available, but is not required when computing it is expensive.

---

## Filtering and Sorting

Filtering and sorting must follow these rules:

1. **Query parameters for filtering** — `?status=active&type=premium`. Simple equality filters use query parameters directly.

2. **Consistent sorting parameter** — `?sort=-created_at` for descending, `?sort=created_at` for ascending. The `-` prefix denotes descending order. Multiple sort fields are comma-separated: `?sort=-created_at,name`.

3. **Complex filtering via documented query syntax** — when filters go beyond simple equality (ranges, inequalities, `IN` clauses), the syntax must be documented and consistent — not ad-hoc per endpoint.

---

## Authentication and Authorization

Auth must follow these rules:

1. **Consistent auth mechanism across all endpoints** — the system uses one auth mechanism (Bearer token, API key, OAuth). Mixing auth mechanisms across endpoints is a governance violation.

2. **Auth required by default; public endpoints are explicit exceptions** — an endpoint is authenticated unless explicitly marked public. The default is secure; openness is the exception that must be justified.

3. **Authorization checked per resource** — auth is not just "can you access this endpoint?" but "can you access this resource?". A user who can read their own profile cannot read another user's profile just because the endpoint is the same.

4. **401 for unauthenticated, 403 for unauthorized** — 401 means "you are not authenticated" (no valid token). 403 means "you are authenticated but not allowed to do this". These must not be confused.

---

## Rate Limiting

Rate limiting must follow these rules:

1. **Rate limits communicated via headers** — every response includes rate limit information:

   ```
   X-RateLimit-Limit: 100
   X-RateLimit-Remaining: 87
   X-RateLimit-Reset: 1699999999
   ```

2. **429 status code when rate limited** — when a consumer exceeds the rate limit, the response is `429 Too Many Requests`, with a `Retry-After` header indicating when to retry.

3. **Consistent rate limit strategy across endpoints** — rate limits are defined by a consistent strategy (per-token, per-IP, per-endpoint) and applied uniformly. Ad-hoc rate limits on individual endpoints are a governance violation.

---

## API Governance and Operational State

The API governance protocol scales with the Operational State, like all doctrine protocols:

1. **Exploratory** — no governance. Exploratory APIs are throwaway. Imposing naming conventions and versioning on a prototype that may be discarded is ceremony that kills exploration.

2. **Formative** — governance when freezing API surface. During the Consolidation Moment (defined in `21_OPERATIONAL_STATES.md`, protocol in `05_CONSOLIDATION_PROTOCOL.md`), when the API surface is being frozen, governance begins to apply. The API is being committed to, and conventions must be established before the freeze.

3. **Stable** — full API governance required. Stable APIs are production contracts. Every rule in this file applies. Breaking changes require versioning and the deprecation protocol. No exceptions.

This scaling prevents two failure modes:

1. Requiring governance in Exploratory — kills exploration with ceremony
2. Not requiring governance in Stable — leaves production APIs inconsistent and unversioned when it matters most

---

## API Review

In Stable state, new or changed APIs must be reviewed before they are released. The review checks:

1. **Naming convention compliance** — resources are nouns, naming is consistent, field naming follows the chosen convention.

2. **Versioning correctness** — breaking changes are versioned, non-breaking changes are not, the versioning strategy is applied consistently.

3. **Error handling consistency** — error format is correct, status codes are correct, error codes are machine-readable, validation errors include field-level details.

4. **Documentation completeness** — the API is documented per `29_DOCUMENTATION_PROTOCOL.md`, including endpoint specs, request/response schemas, authentication, error codes, and examples.

5. **Backward compatibility** — the change does not break existing consumers, or if it does, it is versioned and the old version is maintained during the deprecation period.

An API that fails review is not released. Review is mandatory in Stable state.

---

## API Changes in the Rigid Payload

The Rigid Payload (defined in `20_ENFORCEMENT_LAYER.md`) has four sections. API changes touch two sections:

- **Alterações** — what API surfaces were added, modified, or removed (endpoints, request/response schemas, error codes, auth changes). This is a record of what changed, like any other code change.
- **Enforcement** — how the API changes were verified (contract tests pass, backward compatibility verified, versioning correct, error handling tested).

The Alterações section must include:
- **Endpoints added/modified/removed** — with method, path, and version
- **Schema changes** — request/response schema modifications, with backward compatibility noted
- **Breaking changes** — explicitly flagged, with version bump justification
- **Auth changes** — any changes to authentication or authorization

If a work item does not touch APIs, the Alterações section may state: "No API changes — work item does not touch API surfaces."

---

## API Governance Anti-Patterns

The following are API governance anti-patterns. Any of these in Stable work is a defect that blocks completion.

- **Ad-hoc API design** — each endpoint designed independently, with no consistent naming, error handling, or versioning. The API is a collection of individual choices, not a coherent interface.
- **Breaking change without version bump** — a change that breaks existing consumers is deployed without incrementing the API version. Consumers break silently.
- **No error standard** — errors are returned in different formats, with different field names, different status codes, and different levels of detail. Consumers cannot build reliable error handling.
- **Inconsistent naming** — some endpoints use camelCase, others use snake_case. Some use nouns, others use verbs. The API has no naming convention, or has one that is not followed.
- **No pagination** — endpoints that return collections without pagination. Small datasets work fine; large datasets cause timeouts, memory issues, and poor performance.
- **No rate limiting** — public APIs with no rate limit. A single consumer can overwhelm the service, intentionally or unintentionally.
- **Authentication inconsistency** — some endpoints require authentication, others don't, with no clear pattern. The authentication model is unclear, and security holes emerge.

---

## API Governance and the Consolidation Moment

When work transitions from Formative to Stable state, the Consolidation Moment ritual in `21_OPERATIONAL_STATES.md` requires that the API surface is frozen and governance is applied. Breaking changes require version bumps and migration guides. No work enters Stable state with unreviewed API changes or unversioned breaking changes.

---

## Protocol Success Condition

The API governance protocol has been applied successfully when:

1. All APIs in Stable state follow consistent naming conventions, versioning strategy, error handling format, pagination, filtering, sorting, auth, and rate limiting rules.
2. All APIs in Stable state are versioned correctly — breaking changes are versioned, non-breaking changes are not.
3. All APIs in Stable state are documented completely per the Documentation Protocol.
4. Breaking changes follow the deprecation protocol — old versions are maintained during the deprecation period, not silently removed.
5. New and changed APIs in Stable state pass API review before release.

That is the official success condition of the API governance protocol.

Significant API design decisions — new endpoints, breaking changes, and major version bumps — must be recorded as Architecture Decision Records per `24_ARCHITECTURE_DECISION_RECORDS.md`. See `24_ARCHITECTURE_DECISION_RECORDS.md` for the ADR format and when an ADR is required.

**Anti-pattern:** See ANTI-PATTERN 40 in `16_ANTI_PATTERNS.md`. **Decision rule:** See Rule 16.11 in `08_DECISION_RULES.md`.

---

## Next File

The next file in the doctrine is `33_DATA_GOVERNANCE_PROTOCOL.md`.
