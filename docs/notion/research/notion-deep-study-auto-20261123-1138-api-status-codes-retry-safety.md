# AUTO-147｜Notion API 狀態碼與寫入重試安全（2026-11-23 11:38 Asia/Taipei）

- Run key: AUTO-147-status-codes-20261123-1138; research-only; no Notion / GAS / Cloud Run / Session writes.
- Source: **Status codes — Notion Docs**; https://developers.notion.com/reference/status-codes
- Canonical identity: https://developers.notion.com/reference/status-codes (the /reference/errors URL redirects here; count as one source).
- Source type: official Notion API documentation; accessed 2026-11-23. Publication/update date not independently established.
- Evidence: live source returned 60 numbered lines, inspected lines 20–54 including success, 400–529 error classes, retry caveats, and error payload metadata.
- Reading level: **one independent targeted section-level reading**, NOT a complete deep reading; credited full-depth passes **0/10**.
- Dedup: initial 16-entry register and docs/notion/sources.md checked; full historical research-file semantic audit not completed. Global newly verified unique source count **0** pending audit; do not count /errors and /status-codes twice.

## Verified points and scope
1. Standard error payload distinguishes `code` and `message`; `request_id` is useful for support, and some errors include `additional_data`.
2. 400 missing_version is a version-header issue; 401 unauthorized is invalid token; 403 restricted_resource can mean permission failure **or** workspace block limit.
3. 404 object_not_found may mean the resource is not shared with the integration; it is not sufficient evidence of deletion.
4. 409 conflict_error may indicate collision; state and request parameters should be revalidated before retry.
5. 429 rate_limited means slow down; 529 service_overload explicitly requires honoring Retry-After.
6. 503 service_unavailable can occur when a write succeeded but response building timed out; inspect `additional_data.retry_guidance` before retrying.
7. 503 database_connection_unavailable and 504 gateway_timeout are different conditions; neither proves zero records.
8. 200 means request processed, not that every paginated related record or clinic business rule has been verified.

## Eight falsification hypotheses — NOT observed clinic defects
1. A 404 on Session relation target is treated as deletion instead of access loss.
2. A 403 due to workspace block quota is misdiagnosed as insufficient role permission.
3. A 503 after a create operation is blindly replayed, creating duplicate subsidy-usage rows.
4. A 409 is retried with stale parameters, causing unintended overwrites.
5. A 429/529 retry loop ignores Retry-After and repeatedly fails.
6. A 400 missing_version triggers destructive schema repair rather than header correction.
7. A successful 200 for one data-source query is interpreted as a complete inventory despite next_cursor.
8. A temporary 503/504 is converted to confirmed zero usage instead of unknown/error.

## Evaluation implications (no implementation approval)
Use synthetic tests to distinguish permission, quota, version, conflict, retry, and incomplete-pagination states; preserve unknown vs confirmed zero vs not applicable. For ambiguous write outcomes, verify remote state and retry guidance before deciding to replay. Do not infer live clinic defects or deploy changes from these hypotheses.

## Accounting
Candidate canonical source: 1; targeted independent reading: 1; new hypotheses: 8; verified complete deep reads: 0; verified 10/10 sources: conservative 0/10,000 pending all-history audit. No double-counting of redirected URL.
