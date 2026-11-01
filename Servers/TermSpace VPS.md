---
type: server
provider:
ip: 31.57.92.100
os: Ubuntu 24.04
cost:
renews:
access: password manager → TermSpace VPS root (password auth; 2 vCPU, 4 GB RAM, 40 GB disk)
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
- Upgraded to 2 vCPU / 4 GB / 40 GB (confirmed on the server). Docker images are now ~0.7 GB (api, shared by migrate/scheduler/workers) and ~1.1 GB (web, blog), down from ~3 GB each. Run `docker builder prune -af` if disk gets tight.
- Upload from the local PC to this host was ~3 KB/s through a tar pipe; clone from GitHub on the server instead and send small patches.

## Log

- 2026-11-01: Added. Replaced the unreachable 94.183.191.96.
- 2026-11-01: Disk reached 100% during a web build; freed 8 GB of build cache (now 86% used after the deploy). Upgrade planned by owner.
- 2026-11-01: Owner upgraded the VPS to 2 vCPU, 4 GB RAM, 40 GB disk (was 1 vCPU, 2 GB, 19 GB).
- 2026-11-02: Confirmed 2 vCPU, 3.9 GB RAM, 38 GB disk. 55% used after the slim-image deploy, including old images kept for rollback.
