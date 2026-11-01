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
git pull                       # or git am a small patch for unpushed commits
docker compose build api && docker compose build web   # one at a time, 2 GB RAM
docker compose up -d db redis migrate api web scheduler marketplace-source-worker
```

## Notes

- Compose services running: db, redis, api, web, scheduler, marketplace-source-worker. Not running: blog, email-worker (no Cloudflare email credentials).
- Caddy (`/etc/caddy/Caddyfile`) terminates TLS for termspace.dev (www redirects to apex) and proxies to 127.0.0.1:3000; real client IP taken from CF-Connecting-IP; `TRUST_PROXY=2`.
- Media is local storage, served at `/backend/media`.
- Email and Google sign-in disabled.

## Log

- 2026-11-01: Deployed v.3 at 49b2e50 (cb55e8b from GitHub plus unpushed commit applied as a patch); 35 migrations applied; public HTTPS checked through Cloudflare.
