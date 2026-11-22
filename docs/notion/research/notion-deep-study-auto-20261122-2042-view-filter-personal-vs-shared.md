# AUTO-133｜2026-11-22 20:42 Asia/Taipei｜View 個人篩選與共享設定邊界（研究限定）

- Trace: AUTO-133-20261122-2042-VIEW-PERSONAL-SHARED
- Source title: Database views, filters, sorts & groups | Notion Help
- Original URL: https://www.notion.com/help/views-filters-and-sorts
- Canonical identity: notion-help:views-filters-and-sorts (strip locale, tracking and trailing slash)
- Source type: official Notion Help; accessed 2026-11-22; publication/update date not verified.
- Dedup: GitHub code search for exact slug returned no matches; main research directory checked; this does **not** establish all-history semantic uniqueness. New unique sources formally credited: 0; candidate: 1.
- Reading event: AUTO-133-S01-R1-20261122-2042-SEARCH-EXTRACT-PARTIAL. Read accessible official search-extracted sections: view settings, property visibility, personal versus Save for everyone filters, advanced AND/OR groups up to three levels, and page-opening modes. **Partial text reading only**: full page, images, video, and live UI not inspected. Not full R1, not R2.
- Prior related research: AUTO-128/129/130 cover API Create a view; AUTO-131 Retrieve a view; AUTO-132 List views. This is a distinct Notion Help URL and distinct UI-level reading event, not an API reading counted again.

## Source-grounded observations
1. Settings are per-view: layout, property visibility, filter, sort, group and sub-group. Settings in one view do not automatically propagate to other views.
2. A filter can remain personal until explicitly **Save for everyone**; local operator's visible rows are therefore not proof of a shared view's saved state.
3. Advanced filters support nested AND/OR groups (up to three levels). Nested conditions need explicit verification.
4. Page opening can use side peek, center peek or full page; this is a view-level interaction choice, not evidence of access control.

## New counterexamples to investigate (hypotheses, NOT confirmed clinic defects)
- C01: An administrator temporarily filters to the current subsidy period, assumes the filter was shared, while other staff still see other periods.
- C02: Saving a personal filter for everyone unexpectedly hides historical Sessions from the clinic's default operational view.
- C03: A view is copied; its period filter is assumed to propagate to all other views although each view has independent settings.
- C04: A nested OR condition widens a purported current-period-only filter, exposing records from a previous Price Plan period in the visible list.
- C05: A property is hidden in a view and mistakenly treated as removed from the underlying database or as a security boundary.
- C06: Side-peek and full-page opening differences cause staff to miss the linked episode/plan details despite a correct database record.
- C07: A clinician's personal filter makes an apparently empty list and is misinterpreted as zero eligible sessions, instead of a view-level display state.
- C08: A saved filter produces correct visible rows for one operator but is declared a role-based permission test without checking access as the actual other role.

## Evidence and limitations
- External reading evidence: https://www.notion.com/help/views-filters-and-sorts (search-extracted readable official text, retrieved 2026-11-22).
- This event has no independent screenshot, manual test, Notion workspace access check, source-wide full-text audit, or formal cross-history semantic dedup.
- Metrics this run: candidate source=1; partial reading=1; counterexamples=8; strict complete R1=0; complete R2–R10=0; completed 10/10 sources=0. Conservative previously verifiable total 0/10,000; no global census performed.
- Research-only. No Notion page, DB, View, formula, permissions, GAS, Cloud Run, Session or deployment changes. No redesign authorized.
