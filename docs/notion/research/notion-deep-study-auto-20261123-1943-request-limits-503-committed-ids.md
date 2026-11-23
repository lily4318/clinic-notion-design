# Notion API Request limits｜2026-11-23 19:43 Asia/Taipei｜AUTO-155-20261123-1943-COMMITTED-IDS

## Source identity and reading evidence
- URL: https://developers.notion.com/reference/request-limits
- Title: Request limits — Notion Docs (official)
- Canonical key: notion-developers:reference/request-limits; **existing source**, not a new unique article. Earlier evidence includes AUTO-107 (2026-11-21) and another 2026-11-22 record.
- Retrieval: official readable HTML, 2026-11-23, 254 lines; focused independent second-pass examination of lines 29–68, 205–247, with close reading of lines 208–230 on committed IDs and the limits table. Code snippets read for behavior but not executed. Not a full-document 10/10 deep reading.
- Event: AUTO155-PARTIAL-20261123-1943-503-COMMITTED-IDS; one new targeted **partial** reread. Distinct emphasis from AUTO-107's general throttling summary; not counted as another source or as complete R1–R10.
- Repository state checked immediately before writing: main e3fda510bd50145a5f01ff0de180b0a614e8a843; docs/notion/sources.md blob 4cb54a075ad9243054d899ec715ca2a68140dd80. Research directory checked for same-topic records and target path collision.

## New focused findings / discriminating evidence
1. On some committed-but-503 page/database creations, `additional_data.committed_resource_id` supplies the new object ID; retrieve it instead of replaying POST. For append-children 503, the field is **parent** block ID and `committed_child_ids` enumerates only the direct children created in request order, not nested descendants. This distinction matters for identifying exactly which append took effect.
2. When `retry_guidance` is absent or inconclusive, current remote object state must be checked before a non-idempotent retry; neither 503 nor missing IDs alone proves failure.
3. Per-connection and shared-workspace limits are independent. `public_api_request_blocked` 429 must not be blindly retried; rate-limit reasons can distinguish workspace, endpoint, connection, and MCP limits.
4. 100 relation pages is a per-request value limit, not a total stored relation capacity; property-item pagination remains necessary to avoid undercounting. A 500KB total payload and 1000 block elements limit coexist with smaller field-level limits.

## Eight new targeted falsification cases (not verified defects)
1. POST creates a Session-linked page, returns 503 with committed_resource_id; retry creates duplicate page. Expected safe response: retrieve returned ID and reconcile.
2. Append children returns 503; caller mistakes committed_resource_id (parent) for the newly created child, misses the actual appended records. Check committed_child_ids.
3. Append request creates multiple direct children, nested descendants exist; caller treats committed_child_ids as exhaustive nested subtree. Retrieve descendants separately.
4. Two workers append visually identical blocks; a naive content match attributes the other worker's block to this request. Compare committed_child_ids.
5. A 503 has no retry_guidance; caller assumes no write occurred. Check latest state, use idempotency evidence, stop when ambiguous.
6. Shared workspace throttling occurs despite each worker below its connection budget; independent local rate-limiters fail to coordinate.
7. public_api_request_blocked is treated as temporary and retried repeatedly; must stop and seek support.
8. Relation property contains more than 100 links; first response is treated as complete, understating per-plan usage. Paginate property items and reconcile counts.

## Accounting, constraints, and next checks
- New unique sources **0** (known URL). Independent targeted partial reread **1**. New hypothetical counterexamples **8**. Strict full-depth reads this run **0**. Completed 10/10 sources this run **0**.
- Full historical dedup and independently audited R1–R10 event reconciliation remain incomplete. Conservative verifiable cumulative completed 10/10: **0 / 10,000**; not a claim that every historic file was exhaustively audited.
- No live Notion, GAS, Cloud Run, Session, data, permissions, schema, or view changes; no production tests, no redesign.
- Next research should use a distinct URL or an independently evidenced unfinished reread and audit existing URL aliases before counting.
