# Hub

Cross-project context. Always read [today.md](today.md) first for current focus.

## Active — work (42Lab)
- [la-plateforme](projects/la-plateforme.md) — coaching SaaS, two programs (SaaS + Entrepreneurs)
- [saship](projects/saship.md) — internal client comms/control tool
- [business-school](projects/business-school.md) — client MVP

## Active — personal
- [oumamie](projects/oumamie.md)
- [oumamie-reglementation](projects/oumamie-reglementation.md)

## People
- [Quentin](people/quentin.md) — cofounder, 42Lab
- [Wife](people/wife.md)
- Clients: [Alix](people/clients/alix.md), [Elodie](people/clients/elodie.md), [Léa](people/clients/lea.md), [Fabrice](people/clients/fabrice.md)

## Other
- [All repos](repos.md) — full registry (~25)
- Goals: [pro](goals/pro.md) · [perso](goals/perso.md)
- [Pending](reminders/pending.md) — surface next session

## Conventions
- Small files. Bullets, not prose.
- Update [today.md](today.md) when focus shifts.
- Add to [pending](reminders/pending.md) instead of trying to remember.
- Project files are **thin pointers** to each repo's CLAUDE.md (canonical). Hub holds cross-cutting state only.
- **Conductor worktrees** live at `~/conductor/workspaces/` — when in one, treat it as the same project as the parent repo (link via the `repos.md` registry).
- **Git identities**: pro (42Lab) and perso are separate — see [conventions/git-identities.md](conventions/git-identities.md). Never mix.
- **Umbrella dirs**: some `~/Repos*/` entries are parent dirs grouping multiple sub-repos under one CLAUDE.md — see [conventions/umbrella-dirs.md](conventions/umbrella-dirs.md). Check before assuming a dir is a single repo.

## Future
- **Active reminders** via Resend (already used in la-plateforme): `/schedule` → cron → email. Set up later.
- **Slack scrape** of DMs with Quentin to surface projects/links → see [pending](reminders/pending.md).
