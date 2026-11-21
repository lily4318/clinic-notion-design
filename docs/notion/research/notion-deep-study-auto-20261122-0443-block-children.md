# AUTO-117｜Retrieve block children｜2026-11-22 04:43 Asia/Taipei

- Run identity: AUTO-117-block-children-20261122-0443
- Canonical URL: https://developers.notion.com/reference/get-block-children
- Title: Retrieve block children — Notion Docs
- Source type: official public API reference; actually readable text, not search snippet.
- Dedup: exact canonical URL absent from docs/notion/sources.md at prewrite fetch (blob 4cb54a075ad9243054d899ec715ca2a68140dd80); not yet globally semantically deduplicated across all historical notes, so **candidate only, no globally verified unique increment**.
- Reading scope: API endpoint, paginated response, recursive child retrieval, permissions, error responses, parameters (web retrieved document lines 104–115, 231–243, 332–335, 587–593, 628–678). **Targeted partial reading 1; complete deep reading 0/10**. Do not count multiple analysis angles as separate reads.
- Prior source distinction: Retrieve a block (AUTO-111) is a different endpoint; this note is not a second reading of that page.

## Source-backed findings
1. GET /v1/blocks/{block_id}/children returns **one level only**, with pagination; nested children require further recursive requests.
2. Returned count can be below page_size even when more results remain; use has_more and next_cursor, not row count, for completeness.
3. Read-content capability is necessary; 403 indicates capability restriction. 404 may mean inaccessible, not just nonexistent.
4. Pagination and recursion are separate completeness axes: exhausting top-level cursors alone is insufficient.

## New falsification cases (hypotheses, NOT verified clinic defects)
- F1: Backup exports top-level children only, silently omitting nested toggles and column content.
- F2: First page contains fewer than page_size, crawler prematurely stops despite has_more=true.
- F3: Each nested block has its own cursor but implementation accidentally reuses parent cursor.
- F4: Child block 404 due to access is marked deleted, producing false audit alerts.
- F5: Recursive traversal encounters inaccessible nested content but reports successful full backup.
- F6: Block tree mutates during multi-page traversal, leading to duplicated/missing items; snapshot consistency is not guaranteed by this endpoint and must be independently assessed.
- F7: Synced blocks and child databases are treated as ordinary inline text, causing incomplete content interpretation; verify against Block object specification separately.

## Clinic-specific research implication
A future read-only integrity inventory of administrative workbench content must distinguish (a) direct children scanned, (b) pagination complete, (c) nested traversal complete, and (d) access failures. Do not interpret missing data as zero, deleted, or permission-isolated without further evidence.

## Counting and safety
This round: candidate URL 1, targeted partial reading 1, new counterexamples 7, strict complete reading 0, 10/10 completions 0. Historical verified baseline remains 0/10,000 pending exhaustive audit. Research only; no Notion, GAS, Cloud Run, Session, permission or deployment changes.
