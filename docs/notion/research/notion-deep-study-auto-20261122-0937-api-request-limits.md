# AUTO-122｜Notion API Request limits｜2026-11-22 09:37 Asia/Taipei

Trace: AUTO-122-20261122-0937-REQUEST-LIMITS. Research-only, no Notion or production operations.

Source: https://developers.notion.com/reference/request-limits
Title: Request limits - Notion Docs
Canonical identity: notion-developers:reference/request-limits; exact URL absent from the current main sources.md text, but global historical semantic dedup is NOT complete. Candidate only, not certified new unique source.

Reading event: AUTO122-S01-R1-20261122-0937-HTML-L21-247-TEXT-PARTIAL. Public official HTML opened and inspected (254 lines total). Read API request budget, 429/529 handling, retry examples, 503 write ambiguity, and request property limits. Embedded SDK links and related docs, live behavior and plan-specific application were not inspected; therefore this is a targeted partial textual read, NOT a complete R1 and not a 10/10 completion. No reuse of another run's reading event.

Verified textual findings (source line references):
- L29-57: per-connection 60-second budgets: Business/Enterprise 600/min, other plans 180/min; separate workspace-wide and endpoint-specific throttles. Data source queries about 3/sec/connection. A shared workspace budget can throttle one connection even below its own budget. Retry-After may exceed one minute for workspace limit.
- L59-67: for 429/529 respect Retry-After, bounded retry and jitter; blocked API access is not retriable; 401 and most 400s require corrective action; 403 may be permission or workspace block limit.
- L208-230: a write returning 503 may already have committed. Read retry_guidance and committed_resource_id/committed_child_ids when available; inspect remote state before repeating. Blind POST/PATCH replay risks duplicate records or blocks.
- L231-247: request payload max 1000 block elements and 500KB; rich text content 2000 chars; arrays of block/rich-text objects 100 elements; relation/people input arrays 100. These are per-request input constraints, not proof that the database can hold only 100 related pages. Large response properties need pagination.

Independent counterexamples / falsification targets (research hypotheses, not confirmed clinic bugs):
1. Two independent jobs each stay below 180/min but exhaust shared workspace allowance; per-job green status cannot certify workspace safety.
2. 429 Retry-After ignored or workers independently retry together, creating a second traffic spike.
3. A 503 during append children commits data, naive retry doubles a Session audit block.
4. A 503 during page creation yields committed_resource_id; failure to read back creates duplicate plan-period pages.
5. Treating 100 relation entries/request as an overall database relationship cap leads to false truncation.
6. Treating 403 as always invalid credentials hides workspace block exhaustion; treating 401 as transient wastes retries.
7. Counting a successful 200 on one page of a paginated relation as full backup omits related records.
8. Assuming public API limits imply current clinic plan or observed load: no clinic connection, API logs or live rate tests performed.

Strict counters this run: NEW_GLOBAL_DEDUP_CERTIFIED=0; NEW_SOURCE_CANDIDATE=1; PARTIAL_TEXT_READ=1; INDEPENDENT_FULL_R1=0; FULL_R2_TO_R10=0; COUNTEREXAMPLES=8; FULL_10_OF_10_NEW=0. Last reported fully completed baseline 0/10000, not re-audited historically in this run.

Safety: no Notion page, database, View, formula, relation, permission, GAS, Cloud Run, Session or production changes. No redesign approved or started. Preserve parallel manual and automated work, and do not double-count this reading.
