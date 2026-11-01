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
- Upload from the local PC to this host was ~3 KB/s through a tar pipe; clone from GitHub on the server instead and send small patches.

## Log

- 2026-11-01: Added. Replaced the unreachable 94.183.191.96.
