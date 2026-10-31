---
type: project
status: active
next: Push/PR the creator-notifications phase on v.3, then design direction phase 2 (per-page restyle: landing eyebrow/pastel sections, dashboard density)
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
- 2026-10-31: Design direction phase 1 committed on branch v.3 (not pushed): navy/paper tokens, 12px controls / 16px cards, light panel shadows, pill chips, pastel tints, shared components; `apps/web/DESIGN.md` rewritten from "The Datasheet" to "Paper & Signal" (inspired by anicards.ir, not copied).
- 2026-11-01: Creator moderation notifications implemented and verified locally on v.3 (not pushed): in-app bell with unread count, optional decision email behind the Settings preference, migration `202611010002`. Design phase 1 was pushed with the later branch commits. Local demo data restored; web/API/db left running.
