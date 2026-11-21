# Notion Webhooks｜2026-11-21 19:38｜AUTO-108-20261121-1938-WEBHOOKS

- Scope: Notion design-related external research and GitHub-only progress. No Notion or live-system writes.
- Source URL: https://developers.notion.com/reference/webhooks
- Title: Webhooks — Notion Docs
- Canonical candidate: notion-developers:reference/webhooks. Main sources.md exact URL absent at read time; historical semantic/alternate-URL dedup NOT complete.
- Reading event: AUTO108-S01-20261121-1938-HTML-L20-321-PARTIAL. Official HTML retrieved 2026-11-21; reviewed text sections on event flow, setup, verification, HMAC signature, examples, testing, permissions, delivery delay, and troubleshooting. Embedded screenshots, linked event delivery reference, live verification, and example execution not completed. This is **one partial textual read, not a strict full R1**.

## Verified document-level findings
1. Notion sends HTTPS POST events to a public secure endpoint; events include entity metadata rather than guaranteed current full content. Consumer retrieves updated content using Notion API.
2. Subscription requires verification token; subsequent payloads carry X-Notion-Signature HMAC-SHA256 over raw request body. Re-serializing JSON before verification can break signature matching. Verification token is a secret; do not put real tokens in GitHub.
3. Some content-update events are aggregated with delay; a page title example waits about one minute, test guidance says a minute or two. Real-time means event-driven, not synchronous transaction completion.
4. Comment events require comment-read capability; inaccessible private pages can yield no event. Subscription status must be active.
5. Newer API versions use data_source.schema_updated whereas legacy version used database.schema_updated. Event type compatibility must be version-aware.

## Six new falsification hypotheses (not observed clinic defects)
1. A billing/Session view treats a webhook as proof of final committed content; it can process stale metadata instead of refetching the page and comparing the authoritative record.
2. A dashboard assumes every page edit creates a separate immediate event; aggregated edits cause missed intermediate transitions and false instant synchronization claims.
3. A receiver trusts unsigned or incorrectly signed POST requests; attacker-crafted changes can contaminate billing or usage caches. Validate raw-body HMAC before processing.
4. An integration has access to some pages but not private clinical pages, and assumes silence means no changes; missing permission suppresses expected events.
5. A deployment changes webhook URL after verification without recreating subscription; event delivery stops although application appears healthy.
6. A handler listens only for database.schema_updated after API version migration and misses data_source.schema_updated, leaving price-plan schema caches stale.

## Accounting and boundaries
- NEW_SOURCE_CANDIDATE=1; GLOBAL_UNIQUE_CONFIRMED=0; INDEPENDENT_PARTIAL_TEXT_READ=1; NEW_COUNTEREXAMPLES=6; STRICT_FULL_R1=0; STRICT_R2_TO_R10=0; STRICT_COMPLETE_10_OF_10_THIS_RUN=0.
- Most recently verifiable cumulative strict completed baseline: 0/10,000; no fresh full-history audit performed. This record must not be counted as 10 independent reads.
- Research-only, no endpoint deployment, Notion connection subscription, Notion page/database/View/Formula/permission/Session modification, GAS/Cloud Run or production change. No redesign initiated.
