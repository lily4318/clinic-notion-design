# AUTO 2026-11-21 17:39｜Notion API cursor pagination（研究紀錄）

- Run ID: AUTO-20261121-1739-API-PAGINATION; scope: research-only, no Notion writes.
- Official URL / canonical dedup key: https://developers.notion.com/reference/pagination
- Title: Pagination — Notion Docs; publisher: Notion Developers; accessed: 2026-11-21 (Asia/Taipei).
- Source status: original public HTML text successfully opened; 77 visible lines, main documentation lines 20–70 reviewed once. Embedded interactive SDK behavior and linked articles not executed/read. **Partial text reading, NOT full deep read; independent full 10/10 count contribution = 0**. No claim of globally unique URL until historical semantic dedup audit.

## Verified official text

1. Cursor pagination uses `has_more` and `next_cursor`; the next request must pass `next_cursor` unchanged.
2. A page may contain fewer items than requested while `has_more=true`; never stop based only on returned row count.
3. Most list endpoints allow `page_size` 1–100 (default 100). GET uses query parameters; search/data-source queries use POST body.
4. Keep filters and sort order constant across pages.
5. Special response formats exist for page-property pagination, templates, and view query results. A large data source may reach a result limit even if `has_more=false`, requiring the separate 'Query large data sources' guidance.

## New counterexamples / hypotheses (not production defects)

- E1: An administrative Sessions view returns 43 rows with `page_size=100` and `has_more=true`: stopping at fewer than 100 silently undercounts billable sessions.
- E2: A subsidy ledger changes filters between cursor pages: the union cannot be assumed to represent a consistent single query.
- E3: A large data source returns `has_more=false` after an endpoint limit: treating this as proof of full census risks omitted records; inspect the large-data-source-specific limit.
- E4: Reusing the same cursor for two pages duplicates records and may inflate session counts; enforce cursor progression and deduplicate by page ID.
- E5: A linked View query's pagination is assumed identical to a normal list: the API documents a distinct query_id continuation path.
- E6: A partial page-property response is mistaken for the complete Relation value: follow its documented pagination before concluding a case has no more related sessions.

## Evidence and limits

Direct source: https://developers.notion.com/reference/pagination (main text lines 20–70, retrieved 2026-11-21). These are design-review hypotheses only; no API calls against clinic data, no Notion Schema/View/Formula changes, no GAS/Cloud Run/Session changes. No independent native positive/negative tests. No source accepted as complete 1/10, and no source as 10/10. Prior last reported verifiable 10/10 total: 0/10,000, pending global audit; this file does not change it.
