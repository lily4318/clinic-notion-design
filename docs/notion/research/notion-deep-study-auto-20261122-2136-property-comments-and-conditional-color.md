# AUTO-134｜欄位留言、條件著色與業務審核證據的邊界（2026-11-22 21:36 Asia/Taipei）

- Trace: AUTO-134-20261122-2136-PROPERTY-COMMENT-COLOR
- Source: Notion Help, **Database properties** — https://www.notion.com/help/database-properties
- Canonical: `notion-help:database-properties`; prior AUTO-119 and earlier N11/DS-022. **New unique sources = 0**.
- Independent event: AUTO-134-R-PARTIAL-20261122-2136; re-fetched official body; focused reading of sections *Conditional color* (lines 225–302), *Comment in properties* (303–334), *Assign permissions to people mentioned in person properties* (334–336). This is **one targeted partial reread**, not complete R1–R10. Images, embedded media, links, and real interface were not inspected.
- Before write: refreshed main branch head `eaf5a189473703b78eba39b1c7dcef8449b6e0c7`; reviewed README, AGENTS, system source-of-truth, Notion AGENTS/sources/decision-log/acceptance-status, research directory, and AUTO-119. No Notion access or modification.

## Evidence and new falsification questions

1. Official text: conditional color is per-view; copied views inherit settings, but other views do not automatically inherit. **CE01:** two staff views of the same overdue reimbursement item show different colors; a color-based SOP falsely assumes uniform status.
2. Table view may color one property rather than an entire row, while other supported views use page background. **CE02:** an operator assumes an uncolored adjacent amount is approved because the warning highlights only a status cell.
3. Conditional color supports Formula/Relation/Rollup, but color is presentation rather than a persisted approval decision. **CE03:** an asynchronously recalculated formula changes color without any human sign-off, and is mistaken for an audited approval event.
4. A user needs Can edit content/Can edit/Full access to configure conditional color; view/comment-only roles can see colors but not change the settings. **CE04:** a therapist can see a red row but cannot repair an incorrect color rule; an administrator mistakenly treats that as the therapist's refusal to act.
5. Property comments require an existing value; title, formula, rollup, button and unique ID properties do not support comments. **CE05:** a reviewer tries to annotate an empty eligibility field, fails to attach a property comment, and the workflow silently treats the absence of a comment as approval.
6. Checkbox property comments require opening the database page rather than using the table cell. **CE06:** a table-only checklist asserts every field has a directly accessible inline comment, losing review notes on checkboxes.
7. Comments on property values are not the same as an immutable audit log. **CE07:** a comment documents discussion but cannot independently establish the effective plan period, actor authorization, or preserved historical amount.
8. The help page separately links to access assignment based on person properties, but this run did not read the linked article. **CE08:** treating a person tag as proof of access (or non-access) without separately validating the actual share permissions would be an unsupported inference.

These are **testable hypothetical failure cases**, not verified defects in the clinic. No new design approval follows from them.

## Measurement / boundary

- New unique sources: **0** (existing canonical URL).
- Independent targeted partial reread: **1**; new proposed counterexamples: **8**.
- Strict full reads this run: **0**; independently verified completed 10/10: **0**; carry-forward conservative cumulative baseline **0 / 10,000**, not a full historical recount.
- Limitations: official page's text was retrieved, but all images, linked details, interactive UI, mobile, keyboard, actual roles, formula evaluation and performance were not tested.
- Research and GitHub documentation only. No Notion pages, database, View, formula, permissions, GAS, Cloud Run, Session, or deployment changes. No redesign.
