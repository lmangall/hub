---
type: index
---

# Hub

Cross-project context. Always read [[today]] first for current focus.

## Active — work (42Lab)
- [[la-plateforme]] — coaching SaaS, two programs (SaaS + Entrepreneurs)
- [[saship]] — internal client comms/control tool
- [[business-school]] — client MVP (Alix astrology)

## Active — personal
- [[oumamie]]
- [[oumamie-reglementation]]

## People
- [[quentin|Quentin]] — cofounder, 42Lab
- [[wife|Wife]]
- External contacts (grouped by client org):
  - **Entrepreneurs** (la-plateforme client): [[fabrice|Fabrice]] (boss), [[lea|Léa]] (relay)
  - **Business school / Alix astrology MVP**: [[alix|Alix]], [[elodie|Elodie]]

## Other
- [[repos|All repos]] — full registry (~25)
- Goals: [[pro|pro goals]] · [[perso|perso goals]]
- [[pending]] — surface next session

## Conventions
- Small files. Bullets, not prose.
- Update [[today]] when focus shifts.
- Add to [[pending]] instead of trying to remember.
- Project files are **thin pointers** to each repo's CLAUDE.md (canonical). Hub holds cross-cutting state only.
- **Conductor worktrees** live at `~/conductor/workspaces/` — when in one, treat it as the same project as the parent repo (link via the [[repos]] registry).
- **Git identities**: pro (42Lab) and perso are separate — see [[git-identities]]. Never mix.
- **Umbrella dirs**: some `~/Repos*/` entries are parent dirs grouping multiple sub-repos under one CLAUDE.md — see [[umbrella-dirs]]. Check before assuming a dir is a single repo.
- **Slack channels & ticketing**: registry of channel IDs + the wheel/tick convention for "what's open for X" queries — see [[slack]].

## Future
- **Active reminders** via Resend (already used in la-plateforme): `/schedule` → cron → email. Set up later.
- **Slack scrape** of DMs with [[quentin|Quentin]] to surface projects/links → see [[pending]].

## Vault conventions (Obsidian-compatible)
- Wikilinks `[[name]]` for hub-internal refs. External URLs + `file://` paths stay as standard markdown.
- Each file has minimal YAML frontmatter (`type`, `status`, `side`, `client`, `role` as relevant).
- Aliases let you write `[[Léa]]` and it resolves to `lea.md`.
