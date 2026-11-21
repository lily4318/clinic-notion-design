# AUTO 2026-11-21 13:38｜Database properties｜官方原文部分核讀

- Run ID: AUTO-20261121-1338-DBPROPS; scope: research and GitHub record only.
- Canonical URL: https://www.notion.com/help/database-properties
- Title: Database properties — Notion Help
- Identity: notion-help/database-properties; uniqueness: candidate only; cross-ledger / multilingual semantic dedup NOT verified.
- Retrieval: 2026-11-21; web original page 426 lines; article main text lines 107–336 inspected (including types, create/edit/visibility, date/value, 500-property cap, conditional color, comments and person permissions). Embedded images, interactive UI and linked detail pages NOT inspected. Thus partial main-text read, NOT a full independent R1.
- New source candidate: at most 1, not yet certified unique. Strict FULL_R1=0; FULL_R2–R10=0; FULL_DEEP_PASS_10_OF_10=0. Most recently verifiable cumulative full 10/10: 0/10000 (not full-history audited).

## Grounded rules and counterexamples (research hypotheses, not clinic defects)

1. Property visibility is view-specific (lines 165–173). Hiding Billing values in a clinician view is not an authorization boundary; role-access audit still required.
2. Number property accepts currency formatting (115–118), but formatted amount is not an immutable price snapshot. A historical Session must not silently inherit a changed Price Plan amount; test historical snapshots separately.
3. Unique ID is automatically assigned and cannot be manually changed (135–137). It does not by itself enforce unique Case ID + Price Plan instance membership; duplicates may still be created in a different row.
4. Up to 500 properties per database (214–224). Year-specific columns may eventually hit schema ceiling; this is a capacity warning, not proof current clinic is near limit.
5. Conditional color is configured per view and not automatically inherited by other views (249–293). An abnormal Session highlighted in one view can lack that highlight in another; color must not be sole validation.
6. Last edited timestamp updates automatically (131–134). A record edited for cosmetic reasons is not necessarily the latest performed Session; sort by business date and validated status.
7. Comments are unavailable on formula, rollup, button, name and unique ID properties (303–324). A proposed correction workflow that relies on comments directly in a computed subsidy balance field may be impossible; place review in a supported property/workflow instead.
8. Date can include ranges/timezone and be cleared (185–194). Empty deadline must remain unknown, not be coerced into an approved or zero-duration eligibility state.

## Audit limitations

This reading does not establish actual clinic formula behavior, UX, access control, performance, export/recovery or clinical correctness. No images/interaction/keyboard/screen reader/mobile testing. No Notion, GAS, Cloud Run or Session changes. Full historical and cross-language dedup still outstanding. Do not begin redesign until 10000 unique sources × 10 independent full readings are verifiably completed and user confirms.
