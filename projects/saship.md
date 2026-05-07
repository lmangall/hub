# SaShip

Internal tool 42Lab uses to communicate with and control client work. Each client has their own Slack channel hooked into it.

- Code: [`~/Repos/SaShip/CLAUDE.md`](file:///Users/lmangall/Repos/SaShip/CLAUDE.md)
- Live: <https://eos.saship.42lab.co> (and `/extras`)
- Slack notification skill: `/slack-notify`

## Stakeholders
- [Quentin](../people/quentin.md)
- Used for: business-school clients, la-plateforme clients

## Open threads
- Quentin to review the recent extras update + churn-coaching BI (Léonard pinged him 2026-05-06)

## Decisions / context worth remembering
- **SaSentinel** *(planned, not yet built)*: scheduled Claude agent. Each Thursday morning, re-reads the week's IA conversations, flags ones where users struggled, checks if a Linear ticket already exists, posts a structured report to the SaShip Slack channel. Discussed 2026-04-30. Owner: Léonard?
