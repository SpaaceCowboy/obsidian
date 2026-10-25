---
type: project
status: active
version: Android v0.2.12 (code 23)
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

- APK download: https://13.140.89.146/INSIGHT-online.apk?v=0.2.12
- Private test, no billing, not on the Play Store yet.
- Release notes: `DEPLOYMENT.md` in the Android repo.

## Tasks

- [ ] Check v0.2.12 gestures and haptics on a physical phone; this was not covered by release validation.

## Log

- 2026-10-24: v0.2.8 sound and haptics · v0.2.9 social features · v0.2.10 navigation and reports
- 2026-10-25: v0.2.11 typography and raised buttons (APK only)
- 2026-10-25: v0.2.12 (code 23) published; signed upgrade preserved progress. Source: Android repo DEPLOYMENT.md. Physical-phone and haptic-strength checks remain outstanding.
