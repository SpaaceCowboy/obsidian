---
type: service
server: "[[Crawler VPS]]"
status: running
url: https://scc.rocobroker.com
port:
deployed: 2026-10-26
repo: https://github.com/SpaaceCowboy/seo-automation
---
# Roco SEO

SEO Control Center. Project: [[SEO Automation Ecosystem]].

## How to deploy / update

```sh
sh /opt/roco-seo/app/scripts/operations/compose.sh ps
```

Deploy tested `main` as a versioned release, not the older reference branch. Current code commit: `c9a854f`; image: `roco-seo:staff-main-c9a854f`. Active source `/opt/roco-seo/app` links to `/opt/roco-seo/releases/main-c9a854f/source`. The release directory retains previous source/configuration/image references and guarded `deploy.sh rollback`. Do not roll back after a later release without reviewing the active source-link guard. Database/configuration backups are encrypted under `/opt/roco-seo/backups`; recovery keys remain external.

## Notes

- 

## Log

- 2026-10-25: Added
- 2026-10-26: Deployment attempt stopped before any server changes. Existing-key SSH to the documented server returned Permission denied (publickey). Local changes were pushed as d72e4c1 on codex/phase4-opportunity-engine; this older branch must be reconciled with main before deployment because migration histories differ. Exact running server revision remains unverified. See [[SEO Automation Ecosystem]].
- 2026-10-26: SSH access now verified with the local roco_deploy_v2 key via ssh-agent. API readiness HTTP 200 confirms database and queue ready; API image roco-seo:staff-ga4-host-20261015, worker roco-seo:worker-agent-schema-20261016 and dashboard roco-seo:staff-ui-414a4e1 are healthy. Live opportunity tables match the newer schema rather than the alternate Phase 4 branch. No services restarted, migrations applied or deployment performed. Other hosted applications were left untouched; authenticated dashboard workflows remain unverified.
- 2026-10-26: Deployed reconciled main c9a854f to API, worker and dashboard, all healthy on roco-seo:staff-main-c9a854f. HTTPS sign-in and JS assets return 200, HTTP redirects 308, anonymous control access returns 401, authenticated reads across all sections/datasets return 200. Run 1aed8737-cd7a-429b-a04c-72f845cfbe37 succeeded with opportunities-v2 and duplicate request reuse; incomplete current GSC windows produced no fabricated candidates. No production migration, external inference test or website write; PostgreSQL/Nginx and unrelated services were not recreated. Current Google imports last succeeded October 15. Human staff SSO/MFA browser acceptance is still recommended. Report is in the project repo; see [[SEO manual ledger timestamp validation]].
- 2026-10-26: User confirmed that the normal staff flow opens the live dashboard after deployment. Phases 1–7 were already implemented; this release reconciles stale local work and preserves those systems rather than restarting the project. Phase 8 remains unapproved.
- 2026-10-26: Readiness checklist added (docs/READINESS.md in repo). Caught up GSC to 2026-10-23 (all three datasets), refreshed PageSpeed, and set GOOGLE_SCHEDULES_ENABLED from false to true in /opt/roco-seo/config/production.env (backup: production.env.before-google-schedules-20261026). Worker recreated on the same image and healthy; daily GSC 04:15 UTC, GA4 04:45 UTC, weekly PageSpeed Mon 05:15 UTC. GA4 still empty after 2026-09-28 because the website lost its GA4 tag (see [[RocoBroker Website (com)]]).
- 2026-10-26: Readiness item 2 done. Crawl 3ae51c42 succeeded (217 URLs, 3 x 404, no 5xx); opportunities-v2 run 06e7254f on 2026-09-26..10-23 succeeded with full coverage and updated the same two homepage opportunities (DECAY 65.55, QUICK_WIN "roco" 54.71). Both are below the AI floor of 75, so item 3 needs a calibration decision. GA4 stream 10238429505 / G-PHSEPQ5XHX confirmed by the owner.
