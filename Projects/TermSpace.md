---
type: project
status: active
next:
due:
repo: https://github.com/boyInShadows/termSpace
local: C:\Users\shayan\Documents\ChatGPT\termSpace
---
# TermSpace

Community platform for discovering and publishing agentic coding tools: skills, agents, MCP servers, integrations, rules, prompts, hooks, templates and workflows. English and Persian (RTL). All resources are free.

## Apps

| App | Stack | Port |
|---|---|---|
| `apps/web` | Public catalog and creator platform (Next.js) | 3000 |
| `apps/blog` | Staff-run blog (Next.js) | 3001 |
| `apps/api` | Express + Prisma + PostgreSQL | 4001 |

## Team

- Two maintainers, each working with their own AI agent. Ramtin's side owns `pending.md`. My side owns `apps/web` presentation: landing page, design, motion, dashboard shell.

## Status

- Public HTTPS preview deployed. Email and Google sign-in remain disabled; public access does not establish full launch readiness.
- Remaining work is tracked in the repo: `pending.md`, `readiness.md`, `changelog.md`.

## Deployment

- Server: [[Insight VPS]]
- Domain: https://termspace.13.140.89.146.sslip.io/
- Service: [[TermSpace Public Preview]]

## Log

- 2026-10-24: Startup performance work: precompressed assets, reporting bundle budget
- 2026-10-25: Recorded rejected startup performance trials (last commit)
- 2026-10-25: Recorded public HTTPS preview with automatic certificate renewal, replacing the private SSH-tunnel-only access note. Source: Codex chat Fetch latest from ramtin.
