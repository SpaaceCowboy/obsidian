---
type: project
status: active
next: Connect the remaining services (Telegram token + watchdog, HostVDS probe, Ubuntu VPS target, roco-seo heartbeat wiring), then Phase 5 (host agent, queue checker, /health contracts)
due:
repo:
local: C:\Users\shayan\Documents\projects\pulse
---
# Pulse

Self-hosted health-check dashboard for every deployed service: checks from two vantage points, Telegram alerts routed by role (ADMIN sees all, USER sees Roco targets), heartbeats, 90-day uptime. Deployed as [[Pulse Dashboard]] on [[Pulse VPS]]. Plan: `docs/PLAN.md` in the repo; each phase ends with `PHASE_<N>_NOTES.md`.

## Tasks

- [x] Phases 0-4 (scaffold, checkers, state machine, auth + dashboard, alerts/heartbeats/probe/deploy)
- [x] Create ADMIN user, enable alerts, verify with a real bot, SMTP and watchdog
- [ ] Deploy the probe to HostVDS (95.182.96.28)
- [ ] Phase 5: host agent, queue checker, /health contract in the client portal and roco-seo

## Log

- 2026-10-29: Started (build plan)
- 2026-11-01: Phase 4 done and deployed to https://pulse.termspace.dev
- 2026-11-01: Unblocked the dashboard: termspace repointed to termspace.dev, probe-only SMTP check, self-monitoring added, 4 stale incidents closed, roco-seo heartbeat created. Alerts still off (no bot token).
