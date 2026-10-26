---
type: project
status: active
version: Android v0.2.15 (code 26)
next:
due:
repo: https://github.com/SpaaceCowboy/project-insight
local: C:\Users\shayan\Documents\ChatGPT\insight-android\project-insight
---
# Insight

Tile-swapping puzzle game. Each colour moves in its own fixed direction, and you swap tiles until the board matches the target. 200-level campaign, plus accounts, community puzzles, a puzzle creator, XP and social features.

## Parts

| Part | Where |
|---|---|
| Web game (original) | `Documents\ChatGPT\insight\project-insight` |
| Android app (Kotlin + Jetpack Compose) | `Documents\ChatGPT\insight-android\project-insight` |
| Online backend (TypeScript + PostgreSQL) | `server/` in the Android repo → runs on [[Insight Online]] |

- APK download: https://13.140.89.146/INSIGHT-online.apk?v=0.2.15
- Private test, no billing, not on the Play Store yet.
- Release notes: `DEPLOYMENT.md` in the Android repo.

## Tasks

- [ ] Check v0.2.15 gestures and haptics on a physical phone; this was not covered by release validation.

## Release verification

Run Android emulators on [[Insight VPS]] only, never on the local PC (user preference, 2026-10-26). Prefer the VPS build toolchain as well. Keep test fixtures separate from production and stop them after verification. Project AGENTS.md and DEPLOYMENT.md record the workflow.

## Log

- 2026-10-24: v0.2.8 sound and haptics · v0.2.9 social features · v0.2.10 navigation and reports
- 2026-10-25: v0.2.11 typography and raised buttons (APK only)
- 2026-10-25: v0.2.12 (code 23) published; signed upgrade preserved progress. Source: Android repo DEPLOYMENT.md. Physical-phone and haptic-strength checks remain outstanding.
- 2026-10-26: v0.2.13 (code 24) published with paged collections and layout refinements; fixed compact Rulebook layout and hidden-search accessibility. Verified signed upgrade preserving progress. Final build and tests ran on the VPS; physical-phone/haptic checks remain outstanding.
- 2026-10-26: v0.2.14 (code 25) published with draggable sheets, raised controls, 32-level Journey pages and updated audio/haptics. Fixed repeated-route navigation. VPS unit, preview, compact, online and signed-upgrade checks passed; physical-phone calibration remains outstanding.
- 2026-10-26: v0.2.15 (code 26) and matching backend deployed: raised board platforms, bounded tile dragging, responsive press feedback and 24-item discovery. Fixed consumed-down press cancellation and updated pagination fixtures. VPS unit, preview, compact, online and signed-upgrade tests passed; physical-phone checks remain outstanding.
