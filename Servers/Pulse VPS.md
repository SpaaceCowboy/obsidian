---
type: server
provider:
plan: 1 vCPU, 2 GB RAM, 19 GB disk (2 GB swap added)
ip: 185.92.183.106
os: Ubuntu 24.04 LTS
region:
cost:
renews:
access: ssh deploy@185.92.183.106 with key (root password login still enabled, see Notes) → password manager → Pulse VPS root
---
# Pulse VPS

Core stack for [[Pulse]] (hostname `pulse-termspace-dev`). Docker Compose project `pulse` under `/opt/pulse`.

## Services on this server

```base
filters:
  and:
    - file.inFolder("Services")
    - file.hasLink(this.file)
views:
  - type: table
    name: Services
    order:
      - file.name
      - status
      - url
      - port
      - deployed
```

## Notes

- Firewall (ufw): only 22, 80, 443. Postgres and Redis are not published. fail2ban and unattended-upgrades are on.
- `deploy` user (docker group, key login). Releases in `/opt/pulse/releases/<git sha>`, `/opt/pulse/current` points at the live one, config in `/opt/pulse/.env` (mode 600; secrets live only there).
- Nightly `pg_dump` at 03:17 UTC to `/opt/pulse/backups` (14 days, local only; set `BACKUP_REMOTE` for off-box copies).
- The root password was shared in a chat and should be rotated. `PasswordAuthentication`/`PermitRootLogin` have not been disabled yet (steps in the repo's `deploy/README.md`, last section).
- Outbound SMTP 465 to mail.rocobroker.com times out from here.

## Log

- 2026-11-01: Created. Bootstrapped with `deploy/bootstrap.sh` (Docker 29, deploy user, ufw, swap). First choice 31.59.120.14 was unreachable from the dev machine, so this server is used instead.
