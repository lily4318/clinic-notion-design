# AUTO-164｜Retrieve a data source｜2026-11-24 04:36 Asia/Taipei

- Trace: AUTO-164-20261124-0436-DATASOURCE-READ
- URL: https://developers.notion.com/reference/retrieve-a-data-source
- Title: Retrieve a data source — Notion Developers
- Canonical identity: notion-developers:reference/retrieve-a-data-source
- Access: official readable HTML, 663 lines, checked 2026-11-24.
- Reading event: AUTO164-R01; independently reviewed endpoint definition, ID discovery, response semantics, error and access notes, lines 323–358 and 560–655. **Targeted partial reading only**, not a full-depth R1/10.
- Dedupe: sources.md exact URL absent at last fetch; full historical content URL scan not completed. New unique source credited: 0 pending cross-file reconciliation.

## Verified statements from official documentation
1. GET /v1/data_sources/{data_source_id} returns structural property schema, **not row/page data**; row inspection requires Query a data source.
2. Retrieve database first to enumerate its data_sources IDs/names; database ID and data_source_id are different roles.
3. API response respects connection capabilities and permissions of source and parent database.
4. Related database must also be shared with the integration or relation-derived properties may be **omitted** from returned schema.
5. Linked data sources cannot be retrieved as though they were originals; the original source database must be shared.
6. HTTP 404 can mean nonexistent data source **or inaccessible source**. Do not infer deletion.
7. Official reference currently displays Notion-Version 2026-03-11; this is documentation state, not verification of the clinic integration's version.
8. Readable synced data sources may expose optional sync metadata, which must not be assumed present.

## New falsification scenarios (untested)
1. Schema inventory appears complete but missing Relation properties because target database not shared.
2. Treat a database ID as data source ID, receive failure, wrongly report schema deleted.
3. Linked view renders in UI but integration cannot fetch underlying source, leading to false 'zero rows'.
4. Query property schema and mistakenly infer Session counts/eligibility from definitions alone.
5. A 404 triggers destructive recreation although access sharing is the actual problem.
6. Multiple data sources under one database: selecting first ID silently inspects wrong plan period.
7. Missing optional sync metadata is mistaken for proof the source is not synced.
8. A successful 200 schema read is mistaken for verified formula evaluations, role permissions or actual UI views.

## Application boundary and accounting
For future *authorized* read-only clinic audit, first map database -> data_source ID, verify relation target sharing, then independently inspect rows and views; this record does not assert clinic state.
- Candidate source checked: 1; independent targeted partial reading: 1; hypotheses: 8.
- Strict complete deep-reading events: 0. Verified 10/10 complete: conservative 0/10,000.
- No Notion/GAS/Cloud Run/Session modifications. Shared ledger not overwritten; eventual cross-history dedupe needed.
