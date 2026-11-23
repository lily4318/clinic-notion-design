# AUTO-146｜Notion Webhooks 事件與資料一致性研究（2026-11-23 10:39 Asia/Taipei）

- Run key: AUTO-146-webhooks-20261123-1039; scope: research-only; no Notion / GAS / Cloud Run / Session writes.
- Source: **Webhooks — Notion Docs**; https://developers.notion.com/reference/webhooks
- Canonical URL identity: https://developers.notion.com/reference/webhooks (strip query, fragment, trailing slash).
- Source type: official developer documentation; accessed 2026-11-23; publication/update date not independently confirmed.
- Read evidence: live page returned 326 numbered lines; inspected the workflow, subscription verification, HMAC, tests, permissions, delivery timing and troubleshooting sections (lines 20–321).
- Depth: **one independent structured section-level reading, not a verified full deep reading (0/10)**. This is neither ten separate passes nor an audit of all external references.
- Dedup: exact URL absent from checked docs/notion/sources.md and initial evidence-register; historical research files not fully semantically audited, so **0 globally confirmed new unique sources**. No prior read is promoted.

## Verified source points
1. Webhook notifications contain event metadata, not guaranteed current row/property values; recipient fetches the latest entity using API after verification.
2. Endpoint must be public HTTPS; one-time verification token is used for subscription activation.
3. Event signature uses HMAC-SHA256 over the raw HTTP body, with X-Notion-Signature; reserializing JSON can invalidate verification.
4. Some content events are aggregated and delayed; subscription and capabilities/access control determine which events arrive.
5. In 2025-09-03 API, schema change event is data_source.schema_updated; older database.schema_updated is deprecated.
6. Webhook existence does not establish that downstream reads were complete or the billing/allowance business state was validated.

## Eight falsification cases (hypotheses, not observed defects)
1. Session title or state changes but handler uses metadata as final state without fetching the page.
2. Two rapid edits coalesce into one notification, and a consumer assumes one event equals one changed row.
3. A delayed event is applied after a newer read, overwriting the newer cached state.
4. An unsigned or tampered event reaches processing because signature verification is omitted.
5. JSON reserialization before HMAC creates false negatives and causes legitimate updates to be dropped.
6. Integration loses access to a related data source; absence of events is incorrectly interpreted as no usage.
7. Migration keeps listening only for database.schema_updated and silently misses data_source.schema_updated.
8. Handler receives event but downstream paginated relation/rollup fetch is incomplete; allowance is mistakenly confirmed as zero.

## Implications for future evaluation, NOT implementation authorization
Test notification deduplication and ordering, signature verification, access/capability gaps, fetch-on-event, and incomplete-data states using synthetic isolated data only after explicit authorization. Distinguish unknown, confirmed zero, stale and error; do not derive subsidy approval from webhook arrival.

## Accounting and safety
- Candidate readable sources in this run: 1; partial/structured reads: 1; strict full-depth passes: 0; new falsification cases: 8.
- Confirmed global unique additions: 0 pending complete historical canonical/semantic dedup.
- Confirmed completed sources with 10 independently auditable full reads: conservative 0 / 10,000, pending global audit.
- Research record is independent to avoid concurrent shared-file overwrite. No business system modification or actual operational test.
