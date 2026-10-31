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

Backend for Midori (formerly Insight) (accounts, community puzzles), plus the public APK download at `/INSIGHT-online.apk`. Project: [[Insight]].
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

- 2026-10-27: Deployed username-validation backend and Android v0.2.16. Existing accounts preserved; no migration and feedback remains store-only. Encrypted backup insight-20261027T100417Z.dump.age restored before rollout, with a fresh backup immediately before deployment. Previous runtime: /opt/insight-rollback-before-036; previous APK: /root/insight-apk-rollbacks/INSIGHT-online-v0.2.15-before-creator-memory.apk. Public checksum and live health verified: 13 users, 127 puzzles, all 80 seed puzzles. VPS test processes stopped and isolated test database dropped.

- 2026-10-27: Deployed Android v0.2.17 and backend username validation, UTC daily publishing limit and optional 28-item grid pages. No migration; existing accounts and stored feedback preserved. Encrypted backup insight-20261027T184149Z.dump.age restored before rollout, then a fresh backup ran before deployment. Previous runtime: /opt/insight-rollback-before-037; previous APK: /root/insight-apk-rollbacks/INSIGHT-online-v0.2.16-before-languages.apk. Public checksum and live health verified with 13 users, 129 puzzles and all 80 seed puzzles. VPS test processes stopped; isolated test database dropped.

- 2026-10-28: Deployed Midori v0.2.18 with level badges and case-insensitive share-code list search. No migration; existing app identity/data and stored feedback preserved. Encrypted backup insight-20261028T125110Z.dump.age restored before rollout; fresh backup also ran before deployment. Previous runtime: /opt/insight-rollback-before-038; previous APK: /root/insight-apk-rollbacks/INSIGHT-online-v0.2.17-before-midori.apk. Public checksum and health verified with 14 users, 140 puzzles and all 80 seed puzzles. VPS tests stopped and isolated database dropped.
- 2026-10-31: Deployed Midori v0.2.19 (code 30) and expanded username-filter backend (word list + 6→g). No migration; existing accounts, app identity and stored feedback preserved. Encrypted backup insight-20261031T183029Z.dump.age ran before rollout. Previous runtime: /opt/insight-rollback-before-039; previous APK: /root/insight-apk-rollbacks/INSIGHT-online-v0.2.18-before-039.apk. Public SHA-256 183a0f11…63be200b and health verified with 15 users, 156 puzzles and all 80 seed puzzles. VPS emulator stopped and test database dropped.
