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
- Demo persona for sales/Léa: `sarah-demo@entrepreneurs.com` / `sarah-demo-2@entrepreneurs.com` (creds in Quentin DM)

## Stakeholders
- [Quentin](../people/quentin.md) — cofounder
- Entrepreneurs program direct contacts: [Léa](../people/clients/lea.md), [Fabrice](../people/clients/fabrice.md)
- Active end users (referenced in DMs): Hélène Agati (Excel upload bug on tableau de bord), Alfonso (deal process bug), Abdel (offer-quality completion question)
- Slack: per-client channel, plus the `42lab-X-Entrepreneurs` group

## Open threads
- Should I avoid asking Léa to test/verify things? Or keep doing it via hello-work/priv? *(asked Quentin 2026-05-07)*
- **Admins cleanup**: Quentin to send list of admins to remove or whose role to restrict
- **Refonte agents IA**: 6 unused prompts to clean up or wire — `delivery-experience`, `automatisation-ia`, `leadership-mindset`, `strategie-expansion`, `resolution-client`, `consulting-live` (admin-only by design)
- **Inngest V4 migration** deferred — V4 has breaking changes, only bumped to V3 for now
- **Knowledge Graph** thread (Dassault Systèmes context, big-data + LLM angle)
- **Composio Google Sheet**: agent quality on GSheet creation is poor — improvements made but not enough
- **Coaching questionnaire**: reduce steps + make open questions non-mandatory (with char limit)

## Decisions / context worth remembering
- **HeySimon designer** under trial — "très costaud sur la création d'un branding à partir d'un pitch"; advantage for 42Lab MVP work
- Finances module: multi-account detection broken — virements between own accounts show as top-5 client revenue (Quentin auditing 2026-04-20)
- `next-intl` planned for the la-plateforme stack
- Veille/Concurrents agent uses Firecrawl `crawl` endpoint — picks up SEO URLs not on landing
