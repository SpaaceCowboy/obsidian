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
- No user account existed at deploy time. Create one with `pnpm user create <email> --role ADMIN` (see deploy/README.md).
- Second vantage (probe) not deployed yet: HostVDS runs `deploy/probe/` with the same `HMAC_INGEST_SECRET`.
- Open incidents seen from this server on day one: termspace (sslip.io certificate name mismatch) and roco-email SMTP 465 timeout.
- Monitoring: Caddy and every container have healthchecks; no external watchdog configured yet (`WATCHDOG_URL`).

## Log

- 2026-11-01: Deployed release d7cac5d, then 7119deb (Caddy healthcheck fix: http→https redirect made the IP-based probe fail on a real domain). Migrations 0001–0003 applied, certificate issued, anonymous access verified closed (401/redirect).
