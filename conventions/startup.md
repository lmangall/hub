---
type: convention
---

# Session startup brief

At the start of every Claude session, after reading [[README]] + [[today]], **proactively produce a short brief** (5–10 lines max) covering:

## 1. Calendar — next 48h
- Query Google Calendar (`l.mangallon@gmail.com` primary + `Love calendar` if not too verbose) via MCP for events between now and now+48h
- Note any reminder events firing today
- Flag iCloud-only events from [[calendar]] cache that fall in the window

## 2. Pending / waiting items
- Count items in [[pending]] and the "Waiting on" section of [[today]]
- Show the top 1–2 most urgent inline (full list available on ask)

## 3. New in Slack since last session
- Query the 3 known channels for recent activity (last 24h, or since last hub commit):
  - DM with [[quentin|Quentin]] (`D09PKC6S170`)
  - `#42lab-X-Entrepreneurs` (`C0AFPEVCPR8`)
  - `#business-school-ai` (`C0A773J15FF`)
  - `#astro-dev` (`C09U42NP7JA`)
- For client channels, surface new `:gear:` reactions (open tickets) since last check
- Summarize in 1 line per channel; full content on ask

## 4. Hub state
- `git log --oneline -5` from `~/Repos_P/hub` to show last 5 commits
- Flag any files mentioned in recent commits that might need user attention

## 5. Anomalies / stale items (only if real)
- Goals files still empty (if reminding window appropriate)
- Reminders that have fired with no follow-up action recorded
- Conflicts (e.g., a calendar event vs. a TT/congé)

## Format

Compact. Use a heading like "**Session brief — YYYY-MM-DD**" then 5–10 bullets max. Skip empty sections silently. Don't fire the brief if user clearly opens Claude mid-task (e.g., interrupts with a command in the first message) — wait until they say something open-ended like "hi" or "what's up".

## When NOT to fire
- User immediately gives a specific command/question — answer that first, brief can wait or be skipped
- User has been in continuous conversation (no new session) — brief is for fresh sessions only
- User explicitly says "skip brief" or "no brief today"
