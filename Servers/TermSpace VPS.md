---
type: server
provider:
ip: 31.57.92.100
os: Ubuntu 24.04
cost:
renews:
access: password manager → TermSpace VPS root (password auth; 1 vCPU, 2 GB RAM + 3 GB swap, 19 GB disk)
---
# TermSpace VPS

Runs [[TermSpace]] (web + API) behind Caddy. Domain termspace.dev is proxied by Cloudflare.

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

- Firewall (ufw): 22, 80, 443 only. Docker, Caddy (apt) installed.
- Disk is tight: 19 GB, about 86% used after a deploy. Docker images are ~3 GB each (api, migrate, scheduler, worker, web) plus build cache; a web build needs ~3 GB free. Owner plans to upgrade the server.
- Upload from the local PC to this host was ~3 KB/s through a tar pipe; clone from GitHub on the server instead and send small patches.

## Log

- 2026-11-01: Added. Replaced the unreachable 94.183.191.96.
- 2026-11-01: Disk reached 100% during a web build; freed 8 GB of build cache (now 86% used after the deploy). Upgrade planned by owner.
