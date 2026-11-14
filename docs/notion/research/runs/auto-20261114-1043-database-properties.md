# AUTO 2026-11-14 10:43｜Database properties 既有來源獨立複讀（研究限定）

- Batch ID: AUTO-20261114-1043-PROPERTIES-REREAD
- Source canonical URL: https://www.notion.com/help/database-properties
- Title: Database properties | Notion Help
- Publisher: Notion
- Read date: 2026-11-14 Asia/Taipei
- Dedup: exact canonical URL already present in docs/notion/sources.md; **existing source, not new**. Semantic/history dedup not exhausted.
- Reading event: one independent targeted reading of accessible official HTML text (property types, editing, visibility, limits, conditional colors, comments). No screenshot/UI exercise; **partial reading, not full deep read; not 10/10**.
- Source sections: types (text, number, select, status, date, formula, relation, rollup, timestamps, ID), hide/show, property limit 500, conditional color per view, comments on properties, permissions note. Source checked via live public webpage.

## Evidence and counterexamples (research hypotheses, not live-system defects)
1. Number property supports currency formatting but **display format is not an immutable financial transaction ledger**; historical Billing amounts still require independent provenance.
2. Relation connects pages but does not assert unique patient×plan-period combinations; duplicate subsidy-usage records remain possible without a separate check.
3. Rollup aggregates related properties; an incorrect or missing relation can produce misleading counts, so totals cannot substitute for checking each Session's actual plan-period.
4. Hiding a property via view visibility does not remove underlying data or constitute a confidentiality boundary; role permissions need independent verification.
5. Created/last-edited timestamps are automatic but do not document who approved a subsidy eligibility decision or why; explicit business audit evidence may be needed.
6. Checkbox encodes a binary value, so treating unchecked as 'confirmed no' may collapse unknown/not reviewed into false in a clinical administrative workflow.
7. Conditional colors are per-view, not global; a warning visible in one view might be absent in another, and color alone is not a reliable authorization control.
8. Property limit of 500 is an upper bound, not a performance guarantee; adding one column per year/plan remains a poor substitute for period-keyed records.

## Count and governance
- New unique sources: 0 (already registered).
- Independent targeted partial rereads: 1 (not a qualifying complete deep read).
- Qualifying complete deep reads added: 0; sources reaching 10/10 added: 0.
- Cumulative verified 10/10 total: not independently recomputed across all historical files; do not inflate previously reported 0/10000.
- No Notion pages, databases, views, formulas, permissions, GAS, Cloud Run, or Sessions touched.
- Source snapshot reference: docs/notion/sources.md blob SHA 4cb54a075ad9243054d899ec715ca2a68140dd80 at pre-write check; concurrent work may change main independently.
