---
type: service
server: "[[Insight VPS]]"
status: running
url: https://13.140.89.146
port:
deployed: 
repo: https://github.com/SpaaceCowboy/project-insight
---
# Insight Online

Backend for the Insight Android game (accounts, community puzzles), plus the public APK download at `/INSIGHT-online.apk`. Project: [[Insight]].
Server paths (from DEPLOYMENT.md): `/opt/insight-online` (backups in `/opt/insight-online/backups`), release stages `/opt/insight-release-*`, old APKs in `/root/insight-apk-rollbacks`.

## How to deploy / update

```sh

```

## Notes

- 

## Log

- 2026-10-25: Added
- 2026-10-26: Published Android v0.2.13 at the existing APK URL. Backend, migration 010 and store-only feedback remain unchanged. Previous v0.2.12 APK retained under /root/insight-apk-rollbacks/INSIGHT-online-v0.2.12-before-paging.apk.
- 2026-10-26: Published Android v0.2.14; retained /root/insight-apk-rollbacks/INSIGHT-online-v0.2.13-before-sheets.apk. Backend remains healthy with 13 accounts, 126 puzzles and all 80 seed puzzles; migration 010 and stored feedback unchanged. VPS test processes stopped.
- 2026-10-26: Deployed 24-item discovery backend and Android v0.2.15. Encrypted backup restored successfully before rollout; previous runtime is /opt/insight-rollback-before-035 and previous APK is /root/insight-apk-rollbacks/INSIGHT-online-v0.2.14-before-platforms.apk. No migration; store-only feedback retained. Health verified with 13 accounts, 126 puzzles and all 80 seed puzzles; test processes stopped.
