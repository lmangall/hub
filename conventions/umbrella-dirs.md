# Umbrella directories

Some dirs in `~/Repos/` and `~/Repos_P/` are **umbrellas** — not git repos themselves, but parent dirs that group related sub-repos and hold a project-level `CLAUDE.md` aggregating context across them.

## Detection
A dir is an umbrella when:
- It has a `CLAUDE.md` at root
- It does **not** have a `.git/` at root
- It usually contains one or more sub-dirs that are themselves git repos

```bash
# Quick scan from any parent dir:
for d in */; do [ -f "$d/CLAUDE.md" ] && [ ! -e "$d/.git" ] && echo "umbrella: $d"; done
```

## Known umbrellas
| Umbrella | Location | Sub-repos | Notes |
|----------|----------|-----------|-------|
| `oumamie` | `~/Repos_P/` | `flaveur/` (perso, `lmangall/flaveur`) | Also has root-level loose code (not git-tracked) |
| `SwissEON` | `~/Repos/` | `swisseon-platform`, `swisseon-portal`, `SwissEON_AI`, `docs-notion-user-guide` | Paused project |
| `oumamie_crm` | `~/Repos_P/` | (none currently) | Code without git init |

## Rules for Claude
- **Inside an umbrella**, `git config user.email` returns the global default (pro). **This is misleading** — the real identity lives in each sub-repo's local config.
- Before commits/pushes, always `cd` into the actual sub-repo first.
- The umbrella's `CLAUDE.md` is the cross-cutting view; each sub-repo may have its own.
- When the user mentions a project by umbrella name (e.g. "oumamie"), they may mean the umbrella context, a specific sub-repo, or both — clarify if ambiguous.
- When entering a new dir from `~/Repos*/`, check if it's an umbrella before assuming it's a single repo.
