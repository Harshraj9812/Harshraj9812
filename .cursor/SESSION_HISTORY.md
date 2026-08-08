# Session history & decisions

Append new work here (newest at the bottom). Agents: read this with `.cursor/AGENTS.md` before changing the profile README or stats workflow.

---

## 2026-08-08 — Profile README refresh & private stats

**Transcript:** Cursor chat `f0991ce7-78e5-400d-b6f0-fc88c2bbf25b`

### Timeline

1. **README ← CV**  
   - Updated `README.md` from `Portfolio-Website-ThreeJS/TEMP/Harsh_Raj_Gupta_CV.pdf`.  
   - Aligned About, skills, Accenture seniority (incl. June 2026 promotion), projects, education, certs, achievements, learning.

2. **Broken links**  
   - `github-readme-stats.vercel.app` → **503 DEPLOYMENT_PAUSED** — abandoned for live use.  
   - Quine/stats.quine.sh unreachable — left commented/removed.  
   - Streak Heroku host unreliable — switched to `streak-stats.demolab.com`.  
   - First live fix: `github-stats-extended.vercel.app` for stats + top-langs; activity graph on `github-readme-activity-graph.vercel.app`.  
   - Instagram normalized to `@harsh.raj.2807` (not `harsh.raj.2807_`).

3. **Private repos question**  
   - **Decision:** Public hosts cannot see private repos even with `count_private=true` (they don’t have the user’s token).  
   - User’s most active work is in private repos → public cards undercounted.

4. **Actions for private stats**  
   - **Decision:** Self-generate SVGs via GitHub Actions + classic PAT (`STATS_PAT`: `repo` + `read:user`).  
   - Effort estimate given: ~15–30 min one-time.  
   - Added `.github/workflows/readme-stats.yml` using `stats-organization/github-readme-stats-action@v2`.  
   - README pointed at `./profile/stats.svg` and `./profile/top-langs.svg`.  
   - User created secret and confirmed first run succeeded.

5. **Extend to all four cards**  
   - User saw only stats + top-langs change; asked for streak + activity too.  
   - Temporarily generated `profile/streak.svg` and `profile/activity-graph.svg` in the same workflow.

6. **Private contributions on profile**  
   - User confirmed **“Include private contributions on my profile”** already enabled.  
   - After pull, streak/activity still looked unchanged vs public calendar.

7. **Why streak/activity didn’t “update”**  
   - **Decision / finding:** Streak & activity read GitHub’s **public contribution calendar**. With private contributions already included on the profile, a PAT adds little/no visible change.  
   - Stats & top-langs **do** need the PAT (repo language/commit APIs for private repos).

8. **Revert streak & activity to public hosts**  
   - **Decision (user):** Remove Action generation for streak and contribution graph.  
   - Keep Actions only for `stats.svg` + `top-langs.svg`.  
   - README streak → `https://streak-stats.demolab.com?user=Harshraj9812&hide_border=true`.  
   - README activity → `github-readme-activity-graph.vercel.app` (with existing theme query params).  
   - Deleted local `profile/streak.svg` and `profile/activity-graph.svg`.

9. **Agent docs**  
   - Created agent summary + session history; Cursor rule `.cursor/rules/profile-context.mdc` (`alwaysApply: true`).  
   - **Later same day:** moved docs to `.cursor/AGENTS.md` and `.cursor/SESSION_HISTORY.md` (out of repo root).

### Standing decisions (do not reverse without asking)

| Topic | Decision |
|-------|----------|
| README content source of truth | Latest CV PDF (path above); keep profile in sync when CV changes |
| Stats + top-langs | Local SVGs via Actions + `STATS_PAT` |
| Streak + activity graph | Public hosts only; no Action/PAT |
| Official vercel stats host | Do not use (`DEPLOYMENT_PAUSED`) |
| Profile private contributions toggle | Assumed **on**; required for streak/activity to show private days |
| Secret name | `STATS_PAT` |
| Workflow commit message | `chore: update README stats cards` |

### Open / follow-ups

- None requested. Optional later: rotate PAT, theme tweaks, CV→README sync when CV updates again.
