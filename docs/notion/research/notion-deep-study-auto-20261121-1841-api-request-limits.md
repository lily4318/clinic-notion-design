# Notion API Request limits｜2026-11-21 18:41｜AUTO-107-20261121-1841-API-LIMITS

- Scope: external official documentation study + GitHub-only evidence; no Notion or production system writes.
- Source: https://developers.notion.com/reference/request-limits
- Title: Request limits — Notion Docs
- Canonical identity: notion-developers:reference/request-limits (candidate; global semantic dedup incomplete).
- Evidence: official HTML retrieved 2026-11-21, lines 20–249. Read the rate-limit and size-limit prose, response codes, retry semantics, and request-size table. Code examples reviewed at conceptual level, not executed. No live API or role tests.
- Reading event: AUTO107-S01-PARTIAL-20261121-1841. One independent partial text reading; NOT a full deep reading R1, NOT R2–R10.

## Findings

1. Connection budget is 180 requests/min on non-Business/Enterprise plans and 600 requests/min on Business/Enterprise, plus shared workspace and endpoint-specific throttles; data-source query approximately 3 requests/sec per connection. These are published limits, not observed clinic throughput.
2. HTTP 429 and 529 require Retry-After-aware bounded backoff; blocked 429 should not be retried. A 503 following a write may mean the write committed although the response failed: inspect retry_guidance and read back before any retry.
3. One request payload is capped at 500KB and 1000 block elements; relation values have a 100-page *per-request* limit, not a 100-page total property capacity. Large property responses require pagination.

## Six falsification cases (research hypotheses, not observed defects)

1. Concurrent clinic dashboard refresh and scheduled data pulls may exhaust a shared workspace budget despite each connection being under its individual budget; a local throttle alone cannot prove safety.
2. Treating every 429 as a fixed 1-second wait ignores Retry-After and can amplify repeated throttling, especially shared workspace limits.
3. Blindly replaying Session or billing writes after a 503 may create duplicates because the initial write may have committed. Read-back and idempotency evidence are required before retry.
4. Assuming a Relation has at most 100 linked pages confuses per-request payload limit with stored relationship capacity; usage counts may be underreported if response pagination is skipped.
5. Large batch requests with 1000 blocks or 500KB payload can fail validation even when individual property values satisfy their own limits; partial transaction behavior cannot be assumed.
6. Treating 403 as an ordinary transient outage can hide a permission failure or workspace block limit; classify response before retry.

## Accounting and boundaries

- NEW_SOURCE_CANDIDATE=1 (not yet globally deduplicated); PARTIAL_TEXT_READ=1; COUNTEREXAMPLES=6; STRICT_FULL_R1=0; STRICT_R2_TO_R10=0; COMPLETE_10_OF_10_THIS_RUN=0.
- Last verifiable strict cumulative baseline: 0/10,000 sources completed 10/10, subject to full-history audit.
- Source identity may appear elsewhere under different URLs; no claim of globally unique source. No original code executed, no embedded resource/device/accessibility or clinic-native verification; not full deep study.
- No Notion page, database, View, Formula, Relation, permissions, GAS, Cloud Run, Session, deployment or production write; no redesign authorization.
