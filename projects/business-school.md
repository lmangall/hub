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
- Slack channels:
  - **`#business-school-ai`** (`C0A773J15FF`) — client channel with [[alix|Alix]]
  - **`#astro-dev`** (`C09U42NP7JA`) — internal dev channel ([[quentin|Quentin]] + Léonard); scope docs, roadmaps, technical refs live here

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

## Scope kickoff — Build #2 (V2, current scope)

### Roadmap & briefs (canonical docs)

**Initial scope (Build #1 / V1)** — from `#astro-dev`:
- 📄 **Roadmap pour Alix** ([[quentin|Quentin]], 2026-01-07) — .md file attachment (open in Slack to download)
  → [Slack source](https://42lab.slack.com/archives/C09U42NP7JA/p1767781776498589)
- 📜 **ANNEXE A — Cahier des charges fonctionnel** ([[quentin|Quentin]], 2026-01-06) — full functional spec, 9 sections (objectif, onboarding, chartes, tableau de bord, agents IA, back-office, hors-périmètre, évolutivité). The contract scope.
  → [Slack source](https://42lab.slack.com/archives/C09U42NP7JA/p1767689668003249)

**V2 docs (Build #2 — 60 jours)**:
- 📌 **[[kickoff-brief-alix|Kickoff Brief Build 2]]** (received 2026-05-12 PDF, transcribed) — **most complete** scope doc. Contract context (AR International signed 2026-04-20, kickoff 2026-05-04, ~29k€ HT in 3 payments), pricing tiers (Essentiel 19€ / Pro 29€ / Business 49€), 3 absolute priorities (Swiss Ephemeris roue natale, agents IA context injection, Mon Entourage), differentiating features (Oracle agent, viral Carte de Relation, praticien PDF), exclusions, and Build #3+ vision (6 product visions for long-term).
- 📌 **[[roadmap-alix|Scope détaillé Alix]]** ([[quentin|Quentin]], 2026-05-11) — 8 modules + Build 60j week-by-week (S1–S9). Roadmap sequencing differs from the Kickoff Brief — **reconcile at kickoff**.
  → [Slack source](https://42lab.slack.com/files/U09PR0HB4E8/F0B315W164A/roadmap-alix.md) · local copy: `projects/roadmap-alix.md`
- 📄 **Brief de Kickoff — Build #2 · 60 Jours** (Alix, 2026-05-03) — Alix's V2 brief (Quentin's roadmap-alix.md supersedes for sequencing)
  → [Google Doc](https://docs.google.com/document/d/16L0ah-cy1wewIhIwp5WRzHWAVzNdWCdhqYpzaZDo85E/edit) · [Slack source](https://42lab.slack.com/archives/C0A773J15FF/p1777833804984049)
- 📄 **APPLICATION WEB - 2e itération** (Alix, 2026-03-13) — earlier V2 ideation doc
  → [Google Doc](https://docs.google.com/document/d/1WNu52ZC2w0OzQKFFyOYr636R4ic_k2lS08g4sb0I9FY/edit) · [Slack source](https://42lab.slack.com/archives/C0A773J15FF/p1773417467648589)
- 🎨 **Astro AI Mockup (Manus)** (Alix, 2026-04-21) — V2 visual draft
  → [Mockup home](https://astroaimockup-mophqjds.manus.space/) · [Planning view](https://astroaimockup-mophqjds.manus.space/app/planning) · [Slack source](https://42lab.slack.com/archives/C0A773J15FF/p1776728381449339)
- 📊 **Analyse de Marché PDF** (Alix post-call, 2026-05-04) — Astro/HD/Gene Keys/Numérologie market analysis
  → [Slack source (PDF attached)](https://42lab.slack.com/archives/C0A773J15FF/p1777918881352899)

### Léonard's scope summary
**[Slack source — Quentin DM, 2026-05-04, post-call](https://42lab.slack.com/archives/D09PKC6S170/p1777905161714679)**:
- Lancement possible **weeks 8-14** (*sans* LMS, *sans* API)
- Start with **UI fix**
- Start with **Agent IA**

### V2 pain points (Alix, [Slack source](https://42lab.slack.com/archives/C0A773J15FF/p1777919299976699))
- All chartes on one platform (almost there — astro chart UI/UX still needs optimization)
- Performant AI agents — *agents bluffants*, not generic
- Addictive enough for long-term retention; users ideally create profiles for ALL their own clientes inside the app

### Quentin's call notes (Quentin DM, 2026-05-04)
- [next-intl planned](https://42lab.slack.com/archives/D09PKC6S170/p1777900151828419) (i18n)
- [ActiveCampaign integration](https://42lab.slack.com/archives/D09PKC6S170/p1777905238458879)
- [Concept: "Planning Cosmique / Rétrograde / Transits" — see Manus mockup](https://42lab.slack.com/archives/D09PKC6S170/p1777900793557569)
- ["Platerary Retrogates"](https://42lab.slack.com/archives/D09PKC6S170/p1777900812232979) — placeholder name for retrograde feature

### Strategic asks from Alix
- [PWA for V2](https://42lab.slack.com/archives/C0A773J15FF/p1777140911972179) — Instagram audience, mobile-first inscription
- [Astro-cartographie tab per user](https://42lab.slack.com/archives/C0A773J15FF/p1772799262796419) — recent trend, her differentiation
- [API/white-label for SaaS friend](https://42lab.slack.com/archives/C0A773J15FF/p1773246752891629)
- [Multi-tenant for coaches](https://42lab.slack.com/archives/C0A773J15FF/p1773246933492559) — her audience ARE coaches who'd coach clients via the app

### Inspirations (V2 design references)
- <https://astro-charts.com> — **target chart layout** ([Slack ref](https://42lab.slack.com/archives/C0A773J15FF/p1777918994405039))
- <https://www.costarastrology.com> ([Alix ref](https://42lab.slack.com/archives/C0A773J15FF/p1777919039403599) · [Quentin DM](https://42lab.slack.com/archives/D09PKC6S170/p1777900053055809))
- <https://www.thepattern.com> ([Quentin DM](https://42lab.slack.com/archives/D09PKC6S170/p1777900185302899))

### Technical references
- [kibo-ui image-crop component](https://www.kibo-ui.com/components/image-crop) — Quentin shared 2026-02-11 ([src](https://42lab.slack.com/archives/D09PKC6S170/p1770813811226969))
- [bodygraph.com](https://bodygraph.com/) — Human Design / Gene Keys data source ([src](https://42lab.slack.com/archives/C09U42NP7JA/p1763629452854119))
- [docs.astroapi.cloud](https://docs.astroapi.cloud/) — astrology API ([src](https://42lab.slack.com/archives/C09U42NP7JA/p1763629470072209))
- BODYGRAPH_API_KEY shared in `#astro-dev` ([src](https://42lab.slack.com/archives/C09U42NP7JA/p1763652136234209))
- Code: `github.com/42Lab-co/Astro` (`docs/svg-attempts.md`, `logs/api-requests.log`)

## Currently being worked on (early May)
- **Charte UI/UX V2** — Léonard pushing iterations: degrees on chart, weighted aspect lines (orb-based), Débutant/Standard/Toutes selector (5/10/15 bodies), planet hover isolation, "Positions planétaires" panel, info button, animations. Multiple variants for Alix to choose.

## Deployment
- Production: <https://app.businessschoolalix.com>
- Staging: <https://alix.42lab.co> — reassigned from Production to Preview/All-Branches on 2026-05-12. (Originally set up as prod 2026-01-09, [Slack source](https://42lab.slack.com/archives/D09PKC6S170/p1767954493380649); replaced by `app.businessschoolalix.com` as prod since.)
- Vercel app: <https://business-school-ai-platform.vercel.app>
- Vercel project: <https://vercel.com/42lab/business-school-ai-platform>
- Staging plan: see `.context/staging-setup.md` in the repo

## Open threads
- **Lancement target** (Léonard's 2026-05-04 note in [[quentin|Quentin]] DM): possible weeks 8-14 *sans* LMS / *sans* API. Start with UI fix + Agent IA.
- **AI prompt confusion** — GLOBAL vs Général appear nearly identical; Coach prompt activated unclear; Identité prompt response doesn't seem to match. Needs prompt audit.

## Live ticket status

Don't snapshot tickets here — they go stale. For "what's currently open for Alix?", query the channel using the [[slack]] gear/tick convention. As of 2026-05-07 there were 7 open items (recent UX + data-correctness bugs).
