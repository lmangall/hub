---
type: project
status: active
side: pro
client: entrepreneurs
slack: C0AFPEVCPR8
aliases: [La Plateforme, la-plateforme]
---

# la-plateforme

Coaching SaaS for entrepreneurs. Two programs: **SaaS** (current focus per repo CLAUDE.md) and **Entrepreneurs**.

- Code: [`~/Repos/la-plateforme/CLAUDE.md`](file:///Users/lmangall/Repos/la-plateforme/CLAUDE.md) (canonical, kept up to date)
- Checkouts:
  - `~/Repos/la-plateforme` — main
  - `~/Repos/la-plateforme-SECOND` — Entrepreneurs program work

## URLs
- Entrepreneurs prod: <https://plateforme.entrepreneurs.com> (e.g. `/associes`)
- Entrepreneurs staging: <https://staging-entrepreneurs.42lab.co>
- Landing: <https://get-entrepreneurs.com> (typeform CTA — known typo at 4th word)
- Demo persona for sales/[[lea|Léa]]: `sarah-demo@entrepreneurs.com` / `sarah-demo-2@entrepreneurs.com` (creds in [[quentin|Quentin]] DM)

## Stakeholders
- [[quentin|Quentin]] — cofounder
- Entrepreneurs program: [[fabrice|Fabrice]] (boss), [[lea|Léa]] (relay/PM — sits between 42Lab and Entrepreneurs' end-users, opens tickets, tests features)
- Slack: **`#42lab-X-Entrepreneurs`** (`C0AFPEVCPR8`) — operational channel, multi-deploy/day, [[saship|SaShip]] bot posts deploys + Zendesk tickets here
- Active end users referenced in tickets/DMs: Hélène Agati (Excel upload bug), Alfonso (deal process bug), Abdel (offer-quality), Myriam Daniel (LeanPay redirect bug → goes to wrong portal, should be Learnybox), Aurélie Castel (coach change), Tristan Monthillier (coach access)

## Open threads
- **Refonte agents IA**: 6 unused prompts to clean up or wire — `delivery-experience`, `automatisation-ia`, `leadership-mindset`, `strategie-expansion`, `resolution-client`, `consulting-live` (admin-only by design)
- **Inngest V4 migration** deferred — V4 has breaking changes, only bumped to V3 for now
- **Knowledge Graph** thread (Dassault Systèmes context, big-data + LLM angle)
- **Composio Google Sheet**: agent quality on GSheet creation is poor — improvements made but not enough
- **Coaching questionnaire**: reduce steps + make open questions non-mandatory (with char limit)

## Active work pillars (snapshot from #42lab-X-Entrepreneurs channel late Apr–early May)
- **Landing page builder** *(dominant focus)* — `get-entrepreneurs.com` GTM, Marketplace tab, 30+ templates, theme customizer + Google Fonts, block library "Les plus utilisés", funnel/pages split, cal.eu integration, Noah agent dock, lead capture, demo data for sarah-demo. PLG strategy: free `get-entrepreneurs.com/<page>` URLs drive organic traffic to builder.
- **Finances** — large-file imports (>50), AI categorization on gpt-5-mini, seasonal projection, IBAN tooltip, multi-line category panels, bulk edits, internal transfers via chat
- **Avatar** — 3 personas, mobile drawer, channel mgmt, PDF export, credits infra (phase 2)
- **HubSpot sync** — deals, club members, Vercel completion fixes
- **MAGIC formula** (Offre Irrésistible) — header rename, persistence, agent data access, scoring; **BtoC adaptation open**
- **LeanPay** — sync fixes, Copilote impayé link bug
- **Coaching analytics** — churn dashboard, cohort segmentation, capacity-rule simplification, expert auto-rescheduling
- **Veille / RH / Permissions** — secondary

## Decisions / context worth remembering
- **HeySimon designer** under trial — "très costaud sur la création d'un branding à partir d'un pitch"; advantage for 42Lab MVP work
- Finances module: multi-account detection broken — virements between own accounts show as top-5 client revenue ([[quentin|Quentin]] auditing 2026-04-20)
- `next-intl` planned for the la-plateforme stack
- Veille/Concurrents agent uses Firecrawl `crawl` endpoint — picks up SEO URLs not on landing
- Active client capacity rule reduced to **two criteria**: period + access
- "Depuis un template" page-creation option **removed** (simplification); block variants limit raised to 30
