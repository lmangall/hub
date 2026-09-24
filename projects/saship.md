---
type: project
status: active
side: pro
client: entrepreneurs
aliases: [SaShip]
---

# SaShip

**Tracking repo + roadmap frontend** — passive receiver of commit data from client dev repos. One Next.js app per project, deployed via Vercel, served at `*.saship.42lab.co`.

- Code: [`~/Repos/SaShip/CLAUDE.md`](file:///Users/lmangall/Repos/SaShip/CLAUDE.md)
- Live (Entrepreneurs project branch): <https://eos.saship.42lab.co> + `/extras`
- Slack notification skill: `/slack-notify`

## How it connects to la-plateforme (and other client repos)

```
Client dev repo (la-plateforme)              SaShip tracking repo
├── .github/workflows/                        ├── main (templates only)
│   ├── saship-digest.yml ─── daily 7:30 ──▶ ├── eos (Entrepreneurs branch)
│   └── slack-merge-notify.yml ── on push ──▶ │   ├── content/roadmap.json    (S1–S13 plan)
└── .claude/commands/                          │   ├── content/*.mdx           (deliverables)
    ├── /ship   (commit with prefix)           │   ├── content/commits.mdx     (full log)
    ├── /roadmap (show sprint plan)            │   └── content/extras.json     (off-roadmap asks)
    └── /extra  (add to extras.json)           └── (one branch per client project)
```

- **Daily digest** (cron 7:30 UTC+1, weekdays): collects yesterday's commits → Claude API matches them to roadmap deliverables → writes plain-French changelog entries → updates MDX + extras → Slack digest
- **Merge notify** (on push to main/staging/dev/*): Vercel-aware customer-friendly Slack post. Dev branches in French with author name ("Léonard a ajouté à l'environnement de développement")
- la-plateforme's `[la-plateforme]` (or per-project) commit prefix gates which commits enter which roadmap

## Stakeholders
- [[quentin|Quentin]]
- **Currently used only for: Entrepreneurs program** ([[la-plateforme]] / `la-plateforme-SECOND`), branch `eos`. Other clients ([[business-school]] / [[alix|Alix]]) are not yet wired into SaShip.

## Open threads
- [2026-09-24] Digest repaired (dead since 07-02: `jq` argument limit on `commits.mdx`). It now catches up from `lastSync`, and the first run backfilled 863 commits. Scope-2 statuses were refreshed by hand (17/34 shipped); `/roadmap` reads SaShip live. Details: auto-memory `saship-roadmap-stale-and-digest-broken.md`.
- **Decide:** re-enable or retire the daily Slack digest and AI deliverable matching. They have been dormant since 2026-03-30 because commits stopped carrying `COMMIT_PREFIX=[EOS]`; emptying that variable turns them back on.
- ⚠️ `SLACK_WEBHOOK_URL` is also stored as a plain repo **variable** on la-plateforme, visible to anyone with repo access. Delete it and rotate the webhook (the workflows use the secret).
- Ask [[quentin|Quentin]]: Engram status (marked deployed, but in pilot since 09-17), LMS (staging, still Circle-backed), and whether the 4/09 Paris launch night happened (unverifiable from code).

## Decisions / context worth remembering
- **SaSentinel** *(planned, not yet built)*: scheduled Claude agent. Each Thursday morning, re-reads the week's IA conversations, flags ones where users struggled, checks if a Linear ticket already exists, posts a structured report to the SaShip Slack channel. Discussed 2026-04-30. Owner: Léonard?
- **`main` vs project branches**: improvements to templates/setup → `main`. Per-project content stays on the project branch. Cherry-pick from project → main when something is reusable.
- **Bot commits** all start with `[bot]` (filter with `git log --grep='^\[bot\]'`).

## SaShip bot post patterns (visible in client Slack channels)
- `:rocket: Mise en production effectuée` + bullet list of changes — production deploy
- `:construction: Nouveau déploiement en staging` + "Voir sur staging" link — staging deploy
- `:hammer_and_wrench: *Léonard Mangallon a ajouté à l'environnement de développement*` — dev branch push
- `:ticket: Zendesk x SaShip #11xxx — <title>` — **Zendesk integration**: tickets get auto-posted here
- Tickets without SaShip prefix in the channel are typically manual `/extras` filings
