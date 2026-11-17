# Deploy policy — InstallHub suite (SafeInstall, SafeTradie, TechMate, InstallHub)

Source of truth for the weekly deploy. Moved here on 17 Nov 2026 from the archived Security Suite project (`claude/deploy-policy.md`) so the scheduled tasks can keep it up to date. This folder is blocked from the live site (see `netlify.toml`).

Why: changes are batched into one weekly deploy so Dean gets a single, predictable test each Wednesday morning instead of surprises mid-week. Since 17 Nov 2026 the sites are on Netlify's **Personal plan**: 1,000 credits a month with optional auto top-up. Each production deploy costs 15 credits; branch deploys and Deploy Previews cost nothing. Weekly deploys for all three sites use about 180 credits a month, so credits are no longer the constraint. Dean can push anything out earlier whenever he wants.

## The rule
1. **When Dean asks for a change:** make it, test it, commit it to the **`next`** branch (never `main`), and reply starting with:
   **"Change request logged for weekly deploy."** followed by a one-line summary of what will go out. Add a line to that site's queue below.
2. **Weekly deploy: Tuesday evening (~6:30 pm Melbourne).** If `next` has changes, merge `next` → `main` and push once. That's the single production deploy for the week. If nothing's queued, skip it (no credits used).
3. **Deploying early — Dean's call, any time:**
   - When Dean says "deploy now" / "instant update" / "push it live" (for one site or all), run the same checks as the weekly deploy, fast-forward `main` to `next`, push once, clear the deployed lines from the queue, and confirm. No credit warning needed.
   - For a **critical fix** (site broken, key feature failing — e.g. Send/PDF on SafeInstall, search or Ask TechMate on TechMate, the home page on InstallHub — wrong safety information, privacy or security problem), tell Dean straight away: "⚠️ Critical fix — recommend deploying now", and deploy when he agrees.
4. **Don't deploy early on Claude's own initiative** for small things (wording, colours, tweaks). They wait for Tuesday unless Dean asks.
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
| SafeTradie | siren-soda/safetradie | `main` → safetradie.installhub.org | `next` (created 17 Nov 2026) |
| TechMate | siren-soda/techmate | `main` → techmate.installhub.org | `next` (created 16 Nov 2026 from `main`) |
| InstallHub | siren-soda/installhub | `main` → installhub.org | `next` |

Netlify setting on each site: **Project configuration → Developer settings → Branches and deploy contexts**: Production branch `main`, Branch deploys "Deploy only the production branch". Deploy Previews can stay on (free). Confirmed on InstallHub and one other site 17 Nov 2026; the third not yet checked (low priority: branch deploys are free on the Personal plan).

Netlify environment variable changes only take effect on the next production deploy — add them before Tuesday and they go live with the weekly deploy (no extra credits).

## Queue — SafeInstall
- Queued on `next`: shared "Part of InstallHub" footer (links to TechMate) and a TechMate card in Resources.
- (empty — last deployed Tue 17 Nov 2026)
- Queued on `next`: anonymous GoatCounter visit + action counting (pre-start sent, SWMS sent, PDF saved, app installed) and updated privacy wording. Code: `safeinstall` (safeinstall.goatcounter.com).

## Queue — SafeTradie
- (empty — first deployed Tue 17 Nov 2026, by hand, at safetradie.installhub.org; Resend key added in Netlify)
- Queued on `next`: "How it works" demo address changed to a made-up one (7 Spanner St, Toolville) — the old one was Dean's real suburb.

## Queue — TechMate
- (empty — last deployed Tue 17 Nov 2026 ~9:30 pm, by hand at Dean's request: GoatCounter visit counts and About privacy wording)
- Waiting on Dean: review the Draft guides (quick-fix boxes first); mark reviewed ones `status: reviewed`.

Decided 17 Nov 2026 (Dean): factory default codes that are printed in manufacturer manuals may be published, labelled as factory defaults with the manual and page, plus a reminder to change them. Never publish codes from company in-house docs or any real site's codes.

## Queue — InstallHub
- (empty — last deployed Tue 17 Nov 2026 ~9:30 pm, by hand at Dean's request: SafeTradie card and short link, new tagline "Free tools for security installers and trades", SafeTradie in terms and privacy, GoatCounter wording in privacy)
