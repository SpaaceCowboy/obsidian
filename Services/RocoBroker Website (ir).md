---
type: service
server: "[[Roco VPS]]"
status: running
url: https://rocobroker.ir
port: 3100
deployed: 2026-10-22
repo: https://github.com/SpaaceCowboy/roco-w.git
---
# RocoBroker Website (ir)

Separate six-language marketing shell; blog, dashboard and content synchronization are excluded. Project: [[RocoBroker Website]].

## How to deploy / update

```sh
nginx -t && systemctl reload-or-restart nginx
systemctl restart rocobroker-ir
```

## Notes

- App runs under rocoweb at 127.0.0.1:3100 behind Nginx on ports 80/443; systemd unit: rocobroker-ir.
- Relay DNS is resolved at request time so a .com DNS failure cannot stop Nginx. See [[Nginx upstream DNS blocked IR shell]].

- Contact/lead forms and MT5 downloads forward to .com; keep those upstream services working.
- www redirects to the apex over HTTPS; certificate renewal is automatic.
- Deployment handoff and restart/rollback instructions are in the roco-w repo.

## Log

- 2026-10-25: Added
- 2026-10-25: Captured shell scope and .com dependencies from completed Codex chat Deploy website to new VPS; no live server check performed during this vault update.
- 2026-10-26: Down: 89.46.217.221 refuses connections on ports 80 and 443 (checked from two networks). Not caused by the .com deploy; the server needs a root login to check nginx/rocobroker-ir.

- 2026-10-26: Restored Nginx after its 2026-10-24 startup failed on unresolved rocobroker.com; deployed request-time relay DNS, passed the isolated DNS-failure regression and six-language HTTPS smoke checks. App healthy; certificate valid through 2027-01-20; .com unchanged.
