---
type: project
status: active
version: Midori Android v0.2.19 (code 30)
next:
due:
repo: https://github.com/SpaaceCowboy/project-insight
local: C:\Users\shayan\Documents\ChatGPT\insight-android\project-insight
---
# Insight

Midori (formerly Insight), a tile-swapping puzzle game. Each colour moves in its own fixed direction, and you swap tiles until the board matches the target. 200-level campaign, plus accounts, community puzzles, a puzzle creator, XP and social features.

## Parts

| Part | Where |
|---|---|
| Web game (original) | `Documents\ChatGPT\insight\project-insight` |
| Android app (Kotlin + Jetpack Compose) | `Documents\ChatGPT\insight-android\project-insight` |
| Online backend (TypeScript + PostgreSQL) | `server/` in the Android repo → runs on [[Insight Online]] |

- APK download: https://13.140.89.146/INSIGHT-online.apk?v=0.2.18
- Private test, no billing, not on the Play Store yet.
- Release notes: `DEPLOYMENT.md` in the Android repo.

## Tasks

- [ ] Check v0.2.18 gestures and haptics on a physical phone; this was not covered by release validation.

## Release verification

Run Android emulators on [[Insight VPS]] only, never on the local PC (user preference, 2026-10-26). Prefer the VPS build toolchain as well. Keep test fixtures separate from production and stop them after verification. Project AGENTS.md and DEPLOYMENT.md record the workflow.

## Log

- 2026-10-24: v0.2.8 sound and haptics · v0.2.9 social features · v0.2.10 navigation and reports
- 2026-10-25: v0.2.11 typography and raised buttons (APK only)
- 2026-10-25: v0.2.12 (code 23) published; signed upgrade preserved progress. Source: Android repo DEPLOYMENT.md. Physical-phone and haptic-strength checks remain outstanding.
- 2026-10-26: v0.2.13 (code 24) published with paged collections and layout refinements; fixed compact Rulebook layout and hidden-search accessibility. Verified signed upgrade preserving progress. Final build and tests ran on the VPS; physical-phone/haptic checks remain outstanding.
- 2026-10-26: v0.2.14 (code 25) published with draggable sheets, raised controls, 32-level Journey pages and updated audio/haptics. Fixed repeated-route navigation. VPS unit, preview, compact, online and signed-upgrade checks passed; physical-phone calibration remains outstanding.
- 2026-10-26: v0.2.15 (code 26) and matching backend deployed: raised board platforms, bounded tile dragging, responsive press feedback and 24-item discovery. Fixed consumed-down press cancellation and updated pagination fixtures. VPS unit, preview, compact, online and signed-upgrade tests passed; physical-phone checks remain outstanding.

- 2026-10-27: v0.2.16 (code 27) and matching backend deployed: creator resize memory and phase morphs, anchored puzzle code menus, seven-row bookmarks, media volume for effects and 20-character new usernames. VPS validation passed: 44 unit, 21 preview, four compact, six online tests and signed upgrade preserving progress. Updated publishing test to open the actual puzzle card. Physical-phone checks remain outstanding.

- 2026-10-27: v0.2.17 (code 28) and matching backend deployed: five UI languages, first-play guide, startup splash, adjusted audio, shared username validation, ten new puzzles per UTC day and 28-item bookmarks. Fixed two compile issues and aligned device tests with splash timing and outline-only swipe zones. VPS checks passed: 55 unit, 22 preview, four compact, six online tests and signed upgrade preserving progress. Physical-phone, Android 12+ splash appearance and native-speaker review remain outstanding.

- 2026-10-28: Midori v0.2.18 (code 29) and matching backend deployed; package, signing key and saved data retained. Added tap-through tips, single-touch transition handling, deeper controls, more achievements and list-based share-code search. Fixed profile level badges to agree with progress. VPS checks passed: 55 unit, 22 preview, four compact, six online, signed upgrade, 18 server unit and 20 integration tests. Physical-phone and native-speaker checks remain outstanding.
- 2026-10-31: Midori v0.2.19 (code 30) and matching backend deployed: tip text plates and shrink-to-fit lines, continuous player list, adaptive Journey pages, steady discovery cards on refresh, zen streaming ambience and an expanded username word list with 6→g. No migration. VPS checks passed: 61 Android unit tests, the guide/language device regression, signed v0.2.18→v0.2.19 upgrade, 18 server unit and 20 integration tests. Physical-phone checks and the full device suite remain outstanding.
