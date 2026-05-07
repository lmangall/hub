---
type: convention
---

# Git identities — pro vs perso

Two separate identities. **Never mix.** Never set/override `git config user.*` without asking.

## Pro — 42Lab
- `user.name` = `Leonard Mangallon`
- `user.email` = `leonard@42lab.co`
- SSH host = `github.com` (default), key `~/.ssh/id_ed25519`
- GitHub org = `42Lab-co`
- Default location = `~/Repos/`
- Examples: la-plateforme, SaShip, business_school_ai_platform

## Perso
- `user.name` = `Leonard Mangallon` or `lmangall`
- `user.email` = `l.mangallon@gmail.com`
- SSH host alias = `github.com-personal` (key `~/.ssh/id_ed25519_github_perso`) or `github.com-lmangall` (key `~/.ssh/id_ed25519_lmangall`)
- GitHub user = `lmangall`
- Default location = `~/Repos_P/`
- Examples: oumamie_reglementation, ETH, eur-lex

## Detection (when not obvious)
```bash
git config user.email   # leonard@42lab.co = pro, l.mangallon@gmail.com = perso
git remote -v           # 42Lab-co/* = pro, lmangall/* = perso, host alias matters
```

## Rules for Claude
- **Never** run `git config user.email <something>` or `git config --global user.*` without explicit user request.
- Before any commit/push in an unfamiliar repo, verify the local `user.email` and `remote -v`.
- The global default is pro (`leonard@42lab.co`), so a missing local override = pro by default.
- Path is a hint, not authoritative — trust the repo's own config.
- When **cloning new** repos: ask which identity if not obvious from the URL.

## Known anomalies
- `~/Repos_P/oumamie` — perso location, pro email, no remote. **Resolved**: it's an [[umbrella-dirs|umbrella dir]], not misconfigured. See [[umbrella-dirs]].
