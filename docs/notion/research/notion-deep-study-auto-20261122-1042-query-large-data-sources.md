# AUTO-123｜Query large data sources｜2026-11-22 10:42 Asia/Taipei

- Scope: RESEARCH ONLY. Trace: AUTO-123-20261122-1042-LARGE-DS. No Notion or production mutations.
- Official source: https://developers.notion.com/guides/data-apis/query-large-data-sources
- Title: Query large data sources — Notion Docs.
- Canonical identity: notion-dev:guides/data-apis/query-large-data-sources
- Dedup: exact URL absent from docs/notion/sources.md at checked SHA 4cb54a075ad9243054d899ec715ca2a68140dd80; no similarly named research file in main tree af170bc3a81a5a9d5746ab65af681f9dbf66ffac. Historical semantic dedup incomplete: candidate only, NOT globally unique verified.
- Read event: AUTO123-S01-R1-20261122-1042-HTML-80-249-PARTIAL. Read accessible primary prose, algorithm and code examples, sections on limit detection, created_time windows, unsplittable minute buckets, view queries and alternatives. Did not independently run SDK, inspect cookbook or test against any real data. Thus **targeted substantive text reading, NOT strict full R1**, and no 10/10 credit.
- Primary evidence: source lines 80–249 as retrieved 2026-11-22. Source can change; re-fetch before implementation.

## Verified source statements

1. A data source query caps results at 10,000 **per filter/sort query**, not per data source. It may return `has_more=false` with `request_status.type=incomplete` and `incomplete_reason=query_result_limit_reached`; cursor exhaustion alone does not establish completeness.
2. Check `request_status` on every page. For capped windows, sort by immutable `created_time` ascending, resume with `on_or_after` last timestamp, and deduplicate overlapping boundary rows by page ID. Using `last_edited_time` risks shifting windows.
3. If >10,000 records share the same created_time minute, timestamp-only windows cannot progress; split with another discriminating filter. Top-level OR filters need separate branch queries or a valid rewrite.
4. View queries are also capped but cannot be windowed directly; query the underlying data source with equivalent filters, then apply display ordering locally. Dashboard views without a single data_source_id require separate handling.
5. The guide mentions SDK v5.23.0+ full-row helpers; this was **not independently validated**.

## Counterexamples / falsification scenarios (hypotheses, not confirmed clinic defects)

- CE01: A 25,000-row Session export stops at `has_more=false` after 10,000 and falsely declares a complete backup.
- CE02: A capped result emits incomplete status on an earlier page; checking only the last response loses evidence.
- CE03: Windowing by last_edited_time while billing records are updated silently skips/multicounts records.
- CE04: Two windows overlap on created_time boundary; counting all rows instead of unique IDs overstates usage.
- CE05: Bulk import creates >10,000 rows in the same minute; repeated window query never advances.
- CE06: Existing view has OR filters; naive AND window composition changes the meaning of the original filter.
- CE07: A view query's fixed capped results are treated as exhaustive, ignoring underlying data source.
- CE08: An unsorted/locally resorted export is mistaken for the same order as the live view.
- CE09: A dashboard view lacks single data_source_id; attempting to export it as one source silently omits other sources.

## Research-only implications

For any future independent backup or count verification, require per-page request_status evidence, stable windowing, ID-based deduplication, terminal completeness proof, and separately reported excluded/permission-inaccessible rows. No claim that this clinic currently has >10,000 rows, or that a Notion design change is authorized. The user-approved same-page workflow and plan-period isolation remain unchanged.

## Counts / limitations

- New source candidate: 1 (not globally verified unique).
- Targeted partial text read: 1.
- Strict complete independent R1: 0; strict R2–R10: 0.
- New falsification scenarios: 9.
- This run's fully verified 10/10 completions: 0. Last defensible cumulative benchmark: **0 / 10,000**, pending whole-history audit.
- No private client, financial or raw Notion records collected or stored.
