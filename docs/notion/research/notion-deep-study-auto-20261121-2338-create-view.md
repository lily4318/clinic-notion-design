# AUTO-112｜Notion Create a view API｜2026-11-21 23:38 Asia/Taipei

- Trace: AUTO-112-20261121-2338-CREATE-VIEW-API
- Source: [Create a view — Notion Developers](https://developers.notion.com/reference/create-view)
- Canonical identity: notion-developers:reference:create-view; exact URL absent in current docs/notion/sources.md, decision-log.md, seven core files and GitHub code-search; historical semantic / translated duplicates NOT exhaustively audited. Candidate only, not certified globally unique.
- Evidence: official page fetched 2026-11-21; textual sections lines 904–1204 plus examples 495–585 reviewed; repeated language SDK examples are NOT independent readings.
- Reading event: AUTO112-S01-R1-20261121-2338-HTML-API-CONTRACT-904-1204-PARTIAL. This is one targeted text reading, not complete R1, not R2–R10.
- Endpoint POST /v1/views, latest documented Notion-Version 2026-03-11. Requires data_source_id, name, type; location exactly one of database_id, view_id, create_database. The latter creates linked database block; dashboard widget uses view_id. Connection needs insert and update content capabilities. 404 may mean missing object OR inaccessible connection. 400 for invalid/multiple location selectors. View supports filters, sorts (up to 100), quick_filters, configuration, position and placement; timestamp sorts accepted but not persisted. Documented view types include table, board, list, calendar, timeline, gallery, form, chart, map, dashboard. Evidence URL above; lines 904–1136.
- Research counterexamples (hypotheses, not observed clinic defects):
  1. Passing both database_id and view_id expecting two destinations returns invalid request rather than duplicating two views.
  2. Using create_database for a harmless view test actually creates a linked database block, violating zero-write research scope.
  3. Mistaking a view's filter for role-based access control exposes Session/Billing content to readers with broader source access.
  4. Persisting timestamp sorts as if guaranteed stable ordering leads to inconsistent operational queues; documentation explicitly says timestamp sorts not saved.
  5. Treating 404 as evidence a clinical database was deleted ignores missing integration access.
  6. Assuming configuration visibility changes historical Billing values or snapshots confuses presentation with source data.
  7. Creating many redundant views to simulate a per-user global period selector can diverge from the clinic's same-page direct-display workflow.
- Open validation: exact product plan/API availability, source permission boundaries, version migration, native view UX, screenshot/keyboard/mobile, actual role tests, Notion formula and performance; NO live API POST attempted.
- Counts this run: candidate URL 1, partial independent text read 1, new counterexamples 7, strict full readings 0, 10/10 completed 0. Historical globally verified 10/10 count remains unverified; last reported strict baseline 0/10,000, not a new census.
- Status: RESEARCH_ONLY. No Notion page/database/View/formula/permission changes; no GAS/Cloud Run/Session writes; no redesign approval. Concurrent manual and hourly workflows remain independent.