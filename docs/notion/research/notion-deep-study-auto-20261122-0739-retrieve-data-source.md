# AUTO-120｜Retrieve a data source｜2026-11-22 07:39 Asia/Taipei
Trace: AUTO-120-20261122-0739-DATASOURCE-RETRIEVE-R1-PARTIAL
Source: https://developers.notion.com/reference/retrieve-a-data-source
Title: Retrieve a data source — Notion Developers
Canonical: notion-api:retrieve-a-data-source
Dedup: docs/notion/sources.md exact URL absent at prewrite fetch; entire historical research corpus and semantic duplicates NOT fully checked. New candidate only, not verified unique.
Read event: AUTO120-S01-R1-20261122-0739-HTML-323-656-PARTIAL; official endpoint description, ID discovery, permissions, relations, linked source limitation, errors, API version and response schema reviewed. Code samples and media not exhaustively validated; NOT a full deep read.
Evidence (official HTML lines): 560-561: GET data_sources/{id} returns schema not rows; 564-569: first retrieve containing database then choose data_sources ID; 575-584: 404 can mean inaccessible, relation properties can be omitted if related source not shared, linked source itself cannot be retrieved directly; 597-619: Notion-Version and data_source_id required; 648-654: properties object.
Independent counterexample hypotheses (not verified clinic defects):
1. Reusing database_id as data_source_id causes 404 or wrong endpoint.
2. Treating retrieved schema as Session row data yields false zero-usage.
3. Missing related database sharing silently hides relation properties, falsely interpreted as deleted schema.
4. 404 interpreted as permanent deletion rather than access issue.
5. Linked view/source identifier used as original data source ID fails.
6. Assuming one database contains exactly one data source causes wrong period/plan selection.
7. Omitting explicit Notion-Version causes schema contract drift.
8. Treating optional synced metadata timestamps as confirmed current financial records.
Clinic application: before any future permitted schema audit, distinguish container database, data source, and rows; verify access and API version. No design or operational change authorized.
Counts this run: NEW_SOURCE_CANDIDATE=1; VERIFIED_GLOBALLY_UNIQUE=0; PARTIAL_TEXT_READ=1; FULL_DEEP_R1=0; FULL_10_OF_10=0; COUNTEREXAMPLE_HYPOTHESES=8. Last reported strictly verifiable completed 10/10 baseline: 0/10000, not freshly audited across history.
Safety: GitHub research only; no Notion, GAS, Cloud Run, Session or permission modifications.
