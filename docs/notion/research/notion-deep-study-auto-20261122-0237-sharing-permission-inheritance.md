# AUTO-115｜Notion 分享權限繼承與頁級權限反證（研究限定）
- Trace: AUTO-115-20261122-0237-SHARING-INHERITANCE
- Source: https://www.notion.com/help/sharing-and-permissions
- Title: Sharing & permissions settings (Notion Help)
- Canonical identity: notion-help:sharing-and-permissions
- Duplicate status: EXISTING, previously registered AUTO-97 in docs/notion/sources.md; new unique source count **0**.
- Reading event: AUTO115-S01-20261122-0237-HTML-MAIN-124-381-TARGETED-INDEPENDENT-PARTIAL; read current official main text sections about general access (182–196), levels (197–212), page-level access (233–299), inherited permissions (309–324), and FAQ (379–381). Images, video, product UI and actual permissions not examined. This is a fresh targeted partial reread, **not** a full R2 nor a 10/10 completion.
- Official evidence: Business/Enterprise page-level access uses person or created-by properties and applies across linked views (233–260); broader database/workspace access prevails over narrower page rule (268–299); parent Private move does not automatically remove separately granted subpage access (309–317); public links and cross-linked pages may expose reachability (319–324); Can create applies to database pages on Business/Enterprise and does not grant general visibility into other rows (203–210).
## Independent falsification cases (research hypotheses; no live testing)
1. A therapist's linked view filters Sessions to their name but broad workspace database access still exposes other records; view filter cannot substitute access control.
2. A page-level rule grants only assigned Sessions, while a broader teamspace/workspace Full access silently overrides restriction.
3. Moving a parent administrative page to Private leaves separately shared child pages accessible; parent visibility is not an exhaustive permission audit.
4. Sharing a linked view's container does not itself prove all referenced source records are visible or hidden as expected; test both source and row access.
5. A staff member with Can edit content can modify row values while being unable to change structure; an operation requiring schema edit may fail despite apparent edit access.
6. A Can create role is assumed to exist on a lower plan, or to permit seeing all prior records; both assumptions require plan and role verification.
7. A two-way Relation links a broadly shared page and a sensitive page; the possibility of exposure must be assessed independently of ordinary filters and page layout.
8. A permission audit checks one Share menu but ignores inherited grants, group membership, subpage grants and public links.
## Clinic relevance and boundary
Before any future authorized redesign, distinguish staff/therapist/admin roles, database-level vs page-level vs linked-view access, and the effect of the broadest grant on Sessions, Billing, Care Episodes and subsidy usage. These are **test proposals**, not findings of a clinic security flaw. No clinical or identifying records accessed.
## Metrics
NEW_UNIQUE_SOURCE=0; INDEPENDENT_TARGETED_PARTIAL_REREAD=1; NEW_COUNTEREXAMPLES=8; STRICT_FULL_READ_THIS_RUN=0; STRICT_10_OF_10_THIS_RUN=0; cumulative verified strict 10/10 remains last auditable baseline **0/10000** (no full-history re-audit).
## Scope
Research and GitHub progress record only. No Notion page/database/view/formula/relation/permissions edits, no GAS/Cloud Run/Session/deployment changes. No redesign until threshold and explicit user confirmation.
