# AUTO-159｜Retrieve block children：部分樹與分頁反證｜2026-11-23 23:44 Asia/Taipei

Trace: AUTO-159-20261123-2344-BLOCK-CHILDREN-PARTIAL-TREE
Canonical URL: https://developers.notion.com/reference/get-block-children
Title: Retrieve block children — Notion Docs
Dedup: same canonical URL already recorded in AUTO-117 (2026-11-22 04:43); existing source, new unique count 0.
Source: official readable API reference. Read sections corresponding to lines 104–115, 231–243, 332–335, 587–593, 628–678 on 2026-11-23.
Reading event: AUTO-159-REREAD-01, independent targeted partial reread focusing on completeness, NOT a full-text deep read or completed R2.

## Verified API contract
GET /v1/blocks/{block_id}/children returns only immediate children. Nested children require recursive retrieval. Results are paginated and can be shorter than page_size. Follow has_more and next_cursor. Read-content capability is required; 404 may indicate inaccessible resources rather than nonexistence.

## Eight new counterexample hypotheses
1. Short first page with has_more=true misread as end, silently omitting subsequent blocks.
2. First-level list treated as complete despite nested toggle/column blocks with children.
3. Nested child 404 due to access denied incorrectly classified as absent.
4. Concurrent editing between cursor requests yields potentially inconsistent inventory; no snapshot guarantee stated here.
5. Linked or synced content assumed to be ordinary nested child tree, causing missing or duplicate representation.
6. Linked database block discovery mistaken for proof that Session rows, View filters, and access were audited.
7. Empty children response mistaken for deleted business data without checking parent ID and source.
8. 200 response accepted as completeness without retaining cursors, counts and recursion evidence.

These are untested clinic hypotheses, not observed defects. For a future authorized read-only audit, exhaust cursors for each parent and recurse where appropriate; separately check Data Source rows, Views and permissions.

Run accounting: existing source targeted partial reread=1; newly verified unique=0; new counterexamples=8; full deep reads=0; completed 10/10 this run=0; cumulative verified complete 0/10,000 pending global audit.
Scope: GitHub research-only. No Notion pages, DB, Views, formulas, permissions, GAS, Cloud Run or Session changed.
