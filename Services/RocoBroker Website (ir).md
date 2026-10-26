---
type: service
server: "[[Roco VPS]]"
status: running
url: https://rocobroker.ir
port:
deployed:
repo: https://github.com/SpaaceCowboy/roco-w.git
---
# RocoBroker Website (ir)

Separate six-language marketing shell; blog, dashboard and content synchronization are excluded. Project: [[RocoBroker Website]].

## How to deploy / update

```sh

```

## Notes

- Contact/lead forms and MT5 downloads forward to .com; keep those upstream services working.
- www redirects to the apex over HTTPS; certificate renewal is automatic.
- Deployment handoff and restart/rollback instructions are in the roco-w repo.

## Log

- 2026-10-25: Added
- 2026-10-25: Captured shell scope and .com dependencies from completed Codex chat Deploy website to new VPS; no live server check performed during this vault update.
- 2026-10-26: Down: 89.46.217.221 refuses connections on ports 80 and 443 (checked from two networks). Not caused by the .com deploy; the server needs a root login to check nginx/rocobroker-ir.
