---
type: convention
---

# Slack — channels & in-channel ticketing

## Channel registry

| ID | Name | Project / Person | Notes |
|----|------|------------------|-------|
| `D09PKC6S170` | DM with [[quentin\|Quentin]] | [[quentin]] | Heavy daily, primary async pair-of-eyes |
| `C0AFPEVCPR8` | #42lab-X-Entrepreneurs | [[la-plateforme]] | Operational, multi-deploy/day, [[saship\|SaShip]] bot posts deploys + Zendesk tickets |
| `C0A773J15FF` | #business-school-ai | [[business-school]] | [[alix\|Alix]] client channel — request/feedback flow, V1 in prod + V2 in design |

When user mentions a project or person ("check Alix", "what's pending for Entrepreneurs"), look up the channel here.

## In-channel ticketing convention (Léonard's habit)

Light-touch ticketing on top of normal Slack messages:
- 🛞 **wheel** — open / to be solved
- ✅ **tick** (`:white_check_mark:`) — done

**Assumption (to confirm with user)**: emoji applied as **reaction** on the request message, not in-body. None of the `:wheel:` emoji appear in scraped message bodies, only `:rocket:` (deploy announcements) and `:white_check_mark:` in-body for "I just fixed this".

## Workflow: "what's currently open for X?"

When user asks "what's open for Alix", "what's pending in Entrepreneurs", etc.:
1. Find the channel ID in the registry above
2. `slack_read_channel` with recent limit (~50–100)
3. For each request-style message (typically from the client side), check reactions — use detailed `response_format` since concise may strip reactions
4. Filter: has `:wheel:` (or whichever the user confirms) AND no `:white_check_mark:`
5. Return: date + 1-line summary, grouped by topic if it helps

## Bot / deploy emojis (informational, in message body)

| Emoji | Meaning | Source |
|-------|---------|--------|
| `:rocket:` | New feature shipped | Léonard's deploy posts |
| `:white_check_mark:` | Bug fix done | Léonard's fix posts (in-body, distinct from reaction usage) |
| `:hammer_and_wrench:` | Dev environment push | [[saship\|SaShip]] bot |
| `:construction:` | Staging deploy | [[saship\|SaShip]] bot |
| `:ticket:` | Zendesk × SaShip ticket forwarded | [[saship\|SaShip]] bot |
