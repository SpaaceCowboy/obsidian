---
type: project
status: active
phase: 7.5 / 8
next: Item 3 needs a calibration decision (both opportunities below AI floor 75); website fixes (GA4 tag, wp redirect, poster, broken links) after owner confirms; see docs/READINESS.md
due:
repo: https://github.com/SpaaceCowboy/seo-automation
local: C:\Users\shayan\Documents\ChatGPT\roco-seo
---
# SEO Automation Ecosystem (Roco SEO)

Internal SEO decision system for the [[RocoBroker Website]]. It crawls the site, pulls Google data, finds and scores opportunities, sends recommendations for human approval, logs changes, and measures results at 30, 60 and 90 days.
Loop: Detect → Understand → Prioritize → Recommend → Approve → Execute → Measure → Learn.
The production site stays **read-only**. No change goes out without approval.

## Phases

- [x] 0 Spec and phase gates
- [x] 1 Monorepo foundation (API, worker, DB, logging)
- [x] 2 Crawler and technical SEO engine
- [x] 3 Google data: Search Console, GA4, PageSpeed
- [x] 4 Opportunity engine and scoring
- [x] 5 SEO agents (supervisor, technical, keyword, content, internal linking)
- [x] 6 Recommendations, approval, change ledger, measurement
- [x] 7 Private SEO Control Center dashboard (almost done)
- [ ] 8 Controlled low-risk automation (allowlist, dry-run, kill switch)

## Stack

- Node 22+ / pnpm monorepo, TypeScript
- `apps/api`: Fastify · `apps/worker`: pg-boss jobs · `apps/dashboard`: Next.js
- PostgreSQL 17 + Drizzle (Docker Compose)
- Nginx in front of the dashboard and API (port 8080 → api:4000, dashboard:3000)

## Run locally

```powershell
pnpm install --frozen-lockfile
Copy-Item .env.example .env
docker compose --env-file .env -f infrastructure/compose.yaml up -d postgres
pnpm db:migrate
```

## Deployment

- Server: [[Crawler VPS]] (31.57.24.70)
- Domain: https://scc.rocobroker.com · service note: [[Roco SEO]]
- Deploy method: Tested main source archive, versioned Docker image and reversible Compose rollout; current code release c9a854f. See [[Roco SEO]].

## Docs (in repo)

`docs/PROJECT_BRIEF.md` · `docs/MASTER_PLAN.md` · `docs/ARCHITECTURE.md` · `docs/phases/` · `docs/runbooks/`

## Log

- 2026-09-28: Spec initialized
- 2026-10-04: Snapshot published to `prod` branch
- 2026-10-25: At phase 7.5, almost done
- 2026-10-26: Preserved older local Phase 4 work as d72e4c1 on codex/phase4-opportunity-engine and pushed it. All 50 unit tests, typecheck and lint passed. Main at inspection was 402345f with newer features and a conflicting Phase 4 migration history. No server deployment performed: SSH returned Permission denied (publickey). Previous next step was finishing Phase 7; reconcile branches and access before deploying. See [[Roco SEO]].
- 2026-10-26: SSH access restored using the local roco_deploy_v2 key via ssh-agent. Read-only live verification passed: API readiness reports database and queue ready; API, worker and dashboard containers are healthy. Production already has the newer opportunity schema, 491 page snapshots, 12773 GSC page rows, 901 GA4 rows, 4 PageSpeed samples and 2 opportunities. No deployment or migration performed; reconcile the alternate local Phase 4 implementation before changing production. See [[Roco SEO]].
- 2026-10-26: Reconciled alternate Phase 4 work with main and recovered deployed staff-auth, integration-status, Google/AI and dashboard fixes. Pushed code commit c9a854f and deployed image roco-seo:staff-main-c9a854f to API/worker/dashboard with no production migration. All 187 unit, 35 database integration and 4 browser tests pass. Live authenticated reads and a deduplicated opportunities-v2 run pass; original source counts and two opportunities are preserved. Main is the clean deployment checkout; local master removed, reference Phase 4 branch retained. Current Google imports last succeeded October 15, so refresh evidence before calibration. Full report: docs/MAIN_RECONCILIATION_2026-10-26.md in the repo. See [[Roco SEO]] and [[SEO manual ledger timestamp validation]].
- 2026-10-26: Audit: phases 1–7 live, 7.5 not yet accepted. Readiness checklist in docs/READINESS.md. Item 1 started: GSC current to 2026-10-23, PageSpeed refreshed, Google schedules enabled. GA4 blocked because the website lost its tag on 2026-09-13. Specialist agents (Keyword+Technical first) proposed only after all 7.5 items are verified. See [[Roco SEO]].
