# AUTO-163｜List data source templates｜2026-11-24 03:37 Asia/Taipei

- Trace: AUTO-163-20261124-0337-TEMPLATES-API-READ
- Canonical URL: https://developers.notion.com/reference/list-data-source-templates
- Title: List data source templates — Notion Developers
- Identity: notion-developers:reference/list-data-source-templates
- Scope: public official API reference, not a real clinic Notion inspection
- Reading event: AUTO163-R01; independent targeted **partial** reading of endpoint description, response schema, pagination, permissions, errors and parameters (web page lines 331–354, 580–694). **Not a full deep R1 or any 10/10 pass.**
- Dedupe: latest shared sources.md did not contain this exact URL; decision-log and acceptance-status likewise did not contain it. Historical per-file and semantic deduplication not exhaustive; unique-new **unverified (0 credited)**.
- Source access: official text was readable on 2026-11-24; no authentication or clinic data accessed.

## Verified API observations
1. GET /v1/data_sources/{data_source_id}/templates lists templates readable by the integration; templates are Notion pages, not just catalog entries.
2. Each entry supplies id, name, is_default; at most 100 per response, with has_more/next_cursor and start_cursor for subsequent pages.
3. Name filter is case-insensitive substring match, so filtered results are not an exhaustive template inventory.
4. Only accessible templates are returned; a 404 can indicate missing resource **or** missing connection access.
5. Template properties/content require separate page/markdown retrieval; this listing alone does not prove content integrity, child blocks, safety or permissions.
6. API docs indicate version 2026-03-11; integration version must be verified rather than assumed.

## Counterexamples to validate later (hypotheses, NOT tested)
1. Count only first 100 templates and wrongly conclude all template types inventoried.
2. Interpret a name-filtered empty response as no templates existing.
3. Treat is_default=true as proof that newly created Session pages always have that template applied.
4. Mistake template ID for data_source_id and query the wrong object.
5. Assume listed templates' page bodies are fully accessible or complete without separate content reads.
6. Interpret 404 as deletion and attempt to recreate templates despite an integration sharing problem.
7. Use template names as stable identity and merge distinct IDs with the same name.
8. Assume a template listing verifies the actual Session/Price Plan relation, formulas or role-specific UX.

## Accounting and scope
- Public candidate URL inspected: 1; independently targeted partial read: 1; new hypotheses: 8.
- Strict full-depth reading passes: 0; independently verified 10/10 completed sources: **0/10,000** (conservative historical baseline).
- New unique URL credited: 0 until complete cross-history dedupe.
- No Notion, GAS, Cloud Run, Session, View, schema, permission, formula or live data writes. No redesign authorized.
- Shared source ledger left untouched to avoid overwriting parallel work. This standalone evidence requires eventual ledger reconciliation.
