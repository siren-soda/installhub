# Deploy policy — InstallHub suite (SafeInstall, TechMate, InstallHub)

Source of truth for the weekly deploy. Moved here on 17 Nov 2026 from the archived Security Suite project (`claude/deploy-policy.md`) so the scheduled tasks can keep it up to date. This folder is blocked from the live site (see `netlify.toml`).

Why: all three sites are on Netlify's free plan. Every production deploy costs 15 of 300 monthly credits, and when credits run out every site on the team is paused ("Site not available") until the cycle resets. So production deploys are rationed.

## The rule
1. **When Dean asks for a change:** make it, test it, commit it to the **`next`** branch (never `main`), and reply starting with:
   **"Change request logged for weekly deploy."** followed by a one-line summary of what will go out. Add a line to that site's queue below.
2. **Weekly deploy: Tuesday evening (~6:30 pm Melbourne).** If `next` has changes, merge `next` → `main` and push once. That's the single production deploy for the week. If nothing's queued, skip it (no credits used).
3. **Exceptions — deploy straight away only if:**
   - Dean says "instant update" / "deploy now", or
   - it's a **critical fix** (site broken, key feature failing — e.g. Send/PDF on SafeInstall, search or Ask TechMate on TechMate, the home page on InstallHub — wrong safety information, privacy or security problem). In that case **alert Dean first**: "⚠️ Critical fix — recommend deploying now (uses 15 credits)" and deploy when he agrees.
4. **Never trigger extra deploys** for small things (wording, colours, tweaks). Batch them.
5. Keep the queues below up to date: add a line when a change is logged; clear the deployed lines after each weekly deploy (keep "Waiting on Dean" lines).
6. **Changes only under `docs/` in the InstallHub repo never count as a deploy on their own.** If InstallHub's `next` is ahead of `main` only by commits that touch `docs/`, skip the InstallHub deploy; they go out with the next real InstallHub change.

## Why Tuesday evening
- A full week of changes goes out in one deploy.
- Monday's automatic link check and manual scan have run, so their fixes are in the same batch.
- Evening = installers aren't mid-job; Dean can test Wednesday morning before work.
- Away from Friday, so there's time to fix anything before the weekend.

## Repos / branches
| Site | Repo | Live branch | Queue branch |
|---|---|---|---|
| SafeInstall | siren-soda/safeinstall | `main` → safeinstall.org | `next` |
| TechMate | siren-soda/techmate | `main` → techmate.installhub.org | `next` (created 16 Nov 2026 from `main`) |
| InstallHub | siren-soda/installhub | `main` → installhub.org | `next` |

Netlify setting to confirm on each site: **Project configuration → Build & deploy → Branches and deploy contexts → Branch deploys: "Deploy only the production branch"** (so pushes to `next` cost nothing).

Netlify environment variable changes only take effect on the next production deploy — add them before Tuesday and they go live with the weekly deploy (no extra credits).

## Queue — SafeInstall
- (empty — last deployed Tue 17 Nov 2026)
- Queued on `next`: anonymous GoatCounter visit + action counting (pre-start sent, SWMS sent, PDF saved, app installed) and updated privacy wording. Code: `safeinstall` (safeinstall.goatcounter.com).

## Queue — TechMate
- Queued on `next`: anonymous GoatCounter visit counts (code `techmate`), Ask TechMate AI question counts (count only, never the question), app installs; About page privacy wording.
- (empty — last deployed Tue 17 Nov 2026, by hand)
- Waiting on Dean: review the Draft guides (quick-fix boxes first); mark reviewed ones `status: reviewed`.

Decided 17 Nov 2026 (Dean): factory default codes that are printed in manufacturer manuals may be published, labelled as factory defaults with the manual and page, plus a reminder to change them. Never publish codes from company in-house docs or any real site's codes.

## Queue — InstallHub
- Queued on `next`: privacy policy updated for SafeInstall's and TechMate's GoatCounter visit counts (goes live with the counters).
- (empty — last deployed Tue 17 Nov 2026, by hand)
