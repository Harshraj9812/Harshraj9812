# AGENTS.md — Harshraj9812 profile repo

Special GitHub profile README repo (`Harshraj9812/Harshraj9812`). Renders on https://github.com/Harshraj9812.

**Before changing README, stats cards, or the workflow:** read `.cursor/SESSION_HISTORY.md` for past work and locked decisions. After meaningful work, **append** a dated entry there (what changed + why).

## Purpose

Keep the profile README accurate against the latest CV and present reliable GitHub stats (including private repos where the PAT helps).

## Key files

| Path | Role |
|------|------|
| `README.md` | Profile content shown on GitHub |
| `.cursor/AGENTS.md` | This file — current setup for agents |
| `.cursor/SESSION_HISTORY.md` | Chronological work log + decisions (required reading) |
| `profile/stats.svg` | Stats card (Actions + PAT, includes private) |
| `profile/top-langs.svg` | Top languages card (Actions + PAT) |
| `.github/workflows/readme-stats.yml` | Daily/manual generation of the two local SVGs |
| `.cursor/rules/profile-context.mdc` | Always-on Cursor rule pointing agents here |

CV reference (outside this repo): `Portfolio-Website-ThreeJS/TEMP/Harsh_Raj_Gupta_CV.pdf`

## Stats cards — current setup

| Card | Source | Private data? |
|------|--------|---------------|
| Stats | `./profile/stats.svg` | Yes — `STATS_PAT` + `count_private=true` |
| Top languages | `./profile/top-langs.svg` | Yes — `STATS_PAT` |
| Streak | `streak-stats.demolab.com` | Public contribution calendar only |
| Activity graph | `github-readme-activity-graph.vercel.app` | Public contribution calendar only |

Do **not** regenerate streak/activity in Actions unless the user explicitly asks. Private days already show when GitHub’s **Include private contributions on my profile** is on.

Avoid `github-readme-stats.vercel.app` (often paused). Live fallback if needed: `github-stats-extended.vercel.app`.

## Workflow (`readme-stats.yml`)

- Triggers: cron `30 0 * * *`, `workflow_dispatch`, pushes touching the workflow or `README.md`
- Action: `stats-organization/github-readme-stats-action@v2`
- Commits only `profile/stats.svg` and `profile/top-langs.svg`
- Secret: `STATS_PAT` — classic PAT with `repo` + `read:user`

## Content conventions

- Sync About / skills / experience / education / achievements with the CV
- Contact: website `harshraj.co.in`, Instagram `@harsh.raj.2807`, LinkedIn, `harshraj9812@gmail.com`
- Stats live under **Interesting stats**

## Do not

- Commit secrets or widen PAT scopes without asking
- Re-add streak/activity Action steps without an explicit user request
- Rely on `github-readme-stats.vercel.app`
- Skip updating `.cursor/SESSION_HISTORY.md` after non-trivial decisions
