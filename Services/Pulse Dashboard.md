---
type: service
server: "[[Pulse VPS]]"
status: running
url: https://pulse.termspace.dev
port: 443
deployed: 2026-11-01
repo:
---
# Pulse Dashboard

Self-hosted health-check dashboard (project: [[Pulse]], the project note). Compose stack: `web` (Next.js), `worker` (scheduler, checkers, alerting), `postgres:16`, `redis:7`, `caddy` (Let's Encrypt for pulse.termspace.dev, DNS-only record in Cloudflare).

## How to deploy / update

From the repo (`C:\Users\shayan\Documents\projects\pulse`), full steps in `deploy/README.md`:

```sh
TAG=$(git rev-parse --short HEAD)
git archive --format=tar.gz -o /tmp/pulse-$TAG.tar.gz HEAD
scp /tmp/pulse-$TAG.tar.gz deploy@185.92.183.106:/tmp/
ssh deploy@185.92.183.106 "/opt/pulse/deploy.sh /tmp/pulse-$TAG.tar.gz"
```

`deploy.sh` rolls back to the previous release if the new stack is not healthy within 4 minutes.

## Notes

- Alerts are OFF (`ALERTS_ENABLED=false` in `/opt/pulse/.env`) until a Telegram bot token is set. Incidents are still recorded.
- One ADMIN account exists (`shayan.shoeibzadeh69@gmail.com`, TOTP linked).
- Second vantage (probe) not deployed yet: HostVDS runs `deploy/probe/` with the same `HMAC_INGEST_SECRET`.
- `roco-email` SMTP is probe-only: 25/465/587 to mail.rocobroker.com all time out from this server.
- Monitoring: Caddy and every container have healthchecks; the dashboard checks its own `/api/healthz` + certificate. No external watchdog configured yet (`WATCHDOG_URL`).
- `targets.yaml` is baked into the worker image — any target/check change needs a release, not just a restart.

## Log

- 2026-11-01: Deployed release d7cac5d, then 7119deb (Caddy healthcheck fix: http→https redirect made the IP-based probe fail on a real domain). Migrations 0001–0003 applied, certificate issued, anonymous access verified closed (401/redirect).
- 2026-11-01: Deployed dbe4dfa: termspace moved to `https://termspace.dev` (no Arabic; `/en` still 404s), SMTP check moved to the `hostvds` vantage, added self-monitoring (`pulse-dashboard` json + tls). Closed the 4 stale incidents; open incidents now 0. Created the `roco-seo` heartbeat (grace 25 h, follows the daily 04:15/04:45 UTC jobs) — the push URL was handed to the owner once, only its hash is stored.
