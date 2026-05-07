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

Light-touch ticketing on top of normal Slack messages, applied as **reactions** (not in-body):
- ⚙️ **gear** (`:gear:`) — open / to be solved
- ✅ **tick** (`:white_check_mark:`) — done

**Confirmed working** via test on `#business-school-ai` 2026-05-07. Use `response_format: detailed` — concise mode strips reactions.

Note: `:white_check_mark:` also appears **in-body** (without being a reaction) in Léonard's "I just fixed this" deploy posts. Treat in-body and reaction usage separately. Same for `:rocket:` (only in-body, only as deploy announcement).

## Workflow: "what's currently open for X?"

When user asks "what's open for Alix", "what's pending in Entrepreneurs", etc.:
1. Find the channel ID in the registry above
2. `slack_read_channel` with recent limit (~50–100), `response_format: detailed` (concise strips reactions)
3. For each request-style message (typically from the client side), check reactions
4. Filter: has `:gear:` AND no `:white_check_mark:`
5. Return: date + 1-line summary, grouped by topic if it helps

## Bot / deploy emojis (informational, in message body)

| Emoji | Meaning | Source |
|-------|---------|--------|
| `:rocket:` | New feature shipped | Léonard's deploy posts |
| `:white_check_mark:` | Bug fix done | Léonard's fix posts (in-body, distinct from reaction usage) |
| `:hammer_and_wrench:` | Dev environment push | [[saship\|SaShip]] bot |
| `:construction:` | Staging deploy | [[saship\|SaShip]] bot |
| `:ticket:` | Zendesk × SaShip ticket forwarded | [[saship\|SaShip]] bot |

## TT / congé queries (from [[quentin|Quentin]] DM)

TT and congé planning lives in the [[quentin|Quentin]] DM (`D09PKC6S170`). The user files a periodic summary message there ("préparation de l'été" pattern); Quentin replies with sign-off.

To answer "when am I working from home next?" or "what congés have I taken/planned?":
1. Search the DM with detailed format:
   - `in:<@U08V2JYVCE6> TT`
   - `in:<@U08V2JYVCE6> congé`
   - `in:<@U08V2JYVCE6> télétravail`
   - `in:<@U08V2JYVCE6> "préparation de"` (catches summer/winter/etc planning summaries)
2. Pick the most recent summary message → that's the canonical plan.
3. Cross-reference with [[agenda]] § TT and § Congés.
4. Update [[agenda]] if there's new info, citing the Slack permalink.

## Source permalinks

When filing a doc/link/decision into the hub, **always include a Slack permalink as source** so we can trace back to the original message.

Format: `https://42lab.slack.com/archives/<CHANNEL_ID>/p<TS_NO_DOT>`

Example: TS `1777833804.984049` in channel `C0A773J15FF` → `https://42lab.slack.com/archives/C0A773J15FF/p1777833804984049`

`slack_search_*` and `slack_read_*` (detailed mode) return permalinks directly — copy them as-is. Strip `?thread_ts=...&cid=...` query params for cleanliness unless the permalink targets a thread reply specifically.
