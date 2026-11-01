---
type: service
server: "[[TermSpace VPS]]"
status: running
url: https://termspace.dev
port: 3000
deployed: 2026-11-01
repo: https://github.com/boyInShadows/termSpace
---
# TermSpace

Web app and API of [[TermSpace]]. Blog is not deployed yet.

## How to deploy / update

Code lives in `/opt/termspace` (clone of branch v.3), config in `/opt/termspace/.env` (not in the vault).

```sh
cd /opt/termspace
git fetch origin && git reset --hard origin/v.3   # reset only after `git diff HEAD <pushed commit>` is empty (server may hold a local patch commit)
docker compose build api && docker compose build web   # one at a time, 2 GB RAM; web-only changes need only `build web`
docker compose up -d db redis migrate api web scheduler marketplace-source-worker
```

A web rebuild needs about 3 GB of free disk. If `df -h /` shows more than ~80% used, run `docker builder prune -af` first (build cache only; the next build is slower). The `RUN chown -R` step in the Dockerfiles duplicates `node_modules` and makes images large.

## Notes

- Compose services running: db, redis, api, web, scheduler, marketplace-source-worker. Not running: blog, email-worker (no Cloudflare email credentials).
- Caddy (`/etc/caddy/Caddyfile`) terminates TLS for termspace.dev (www redirects to apex) and proxies to 127.0.0.1:3000; real client IP taken from CF-Connecting-IP; `TRUST_PROXY=2`.
- Media is local storage, served at `/backend/media`.
- Email and Google sign-in disabled.

## Log

- 2026-11-01: Deployed v.3 at 49b2e50 (cb55e8b from GitHub plus unpushed commit applied as a patch); 35 migrations applied; public HTTPS checked through Cloudflare.
- 2026-11-01: Deployed v.3 at ee4eb2b (simplified creator listing editor, web image only, no migrations). Server checkout reset to origin/v.3, replacing the local patch commit 49b2e50 (identical tree to pushed 82a39f3). Disk hit 100% mid-build; fixed with `docker builder prune -af`. Site, /explore and the editor route return 200.
