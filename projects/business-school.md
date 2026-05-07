---
type: project
status: active
side: pro
client: business-school
slack: C0A773J15FF
aliases: [Business School, Alix astrology MVP]
---

# Business School (Alix astrology MVP)

42Lab MVP for client **[[alix|Alix]]** — a **multi-pillar astrology product** (note: repo name "business_school_ai_platform" reflects client sector, not product domain).

- Code: [`~/Repos/business_school_ai_platform/CLAUDE.md`](file:///Users/lmangall/Repos/business_school_ai_platform/CLAUDE.md)
- Feature branch: `~/Repos/business_school_ai_platform-ai-feature`
- **Not on [[saship|SaShip]]** (yet). SaShip currently wires Entrepreneurs only.
- Slack: **`#business-school-ai`** (`C0A773J15FF`) — see [[slack]] for channel registry + ticketing

## Product

**V1** is in production with paying customers (€700–880/month — automated Stripe → access flow, occasionally has gaps requiring manual addition).

**Pillars** (all on one platform):
- Astrologie (system: **Placidus** — intercepted signs are a value-add vs equal-house systems)
- Human Design
- Gene Keys
- Numérologie

**V2** in design since ~2026-03-13. Alix's pain points (her 2026-05-04 message):
- All chartes on one platform (almost there, astro chart UI/UX needs optimization)
- Performant AI agents — current complaints about generic responses, prompt confusion (GLOBAL vs Général vs Identité)
- Addictive enough for long-term subscriptions, ideally so users create profiles for *all their own clients* on it

## Strategic asks from Alix (V2 + roadmap)
- **Astro-cartographie** — Alix wants this added (recent trend, her differentiation vs competitors)
- **PWA** for V2 — her audience comes from Instagram, mobile-first inscription
- **API / white-label** — Alix's friend (SaaS founder) wants integration; could open white-label licensing tier
- **Multi-tenant for coaches** — her audience are coaches themselves; offer them a way to coach their own clients via the app

## Stakeholders
- Clients: [[alix|Alix]] (decision-maker), [[elodie|Elodie]], Adrien (team member, briefly mentioned)
- [[quentin|Quentin]] — cofounder
- Active end users referenced in tickets: Audrey Bisiaux (chemin de vie data bug), Emma, Gabrielle, Fanny, Wilkin Lora
- Tagline of Alix's team emails: "les astres sont avec moi" (in-character with the product)

## V2 design references
- <https://astro-charts.com> — **target chart layout** (Alix wants non-overlapping placements like this)
- <https://www.costarastrology.com> — co-star
- <https://www.thepattern.com> — the pattern
- <https://astroaimockup-mophqjds.manus.space> — Alix's Manus V2 mockup
- V2 doc 1: <https://docs.google.com/document/d/1WNu52ZC2w0OzQKFFyOYr636R4ic_k2lS08g4sb0I9FY>
- V2 doc 2 (recap pain points): <https://docs.google.com/document/d/16L0ah-cy1wewIhIwp5WRzHWAVzNdWCdhqYpzaZDo85E>
- Concepts brainstormed (in [[quentin|Quentin]] DMs): "Planning Cosmique", "Platerary Retrogates" (name play on Planetary Retrogrades), Transits

## Currently being worked on (early May)
- **Charte UI/UX V2** — Léonard pushing iterations: degrees on chart, weighted aspect lines (orb-based), Débutant/Standard/Toutes selector (5/10/15 bodies), planet hover isolation, "Positions planétaires" panel, info button, animations. Multiple variants for Alix to choose.

## Open threads
- **Lancement target** (Léonard's 2026-05-04 note in [[quentin|Quentin]] DM): possible weeks 8-14 *sans* LMS / *sans* API. Start with UI fix + Agent IA.
- **AI prompt confusion** — GLOBAL vs Général appear nearly identical; Coach prompt activated unclear; Identité prompt response doesn't seem to match. Needs prompt audit.

## Live ticket status

Don't snapshot tickets here — they go stale. For "what's currently open for Alix?", query the channel using the [[slack]] gear/tick convention. As of 2026-05-07 there were 7 open items (recent UX + data-correctness bugs).
