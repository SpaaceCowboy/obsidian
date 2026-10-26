---
type: service
server: "[[Host1]]"
status: running
url: https://rocobroker.com
port:
deployed: 2026-10-26
repo: https://github.com/SpaaceCowboy/roco-w.git
---
# RocoBroker Website (com)

Main site. Project: [[RocoBroker Website]].

## How to deploy / update

Build a new release dir under `/opt/rocobroker-releases/` from `main` (upload a `git archive`; the VPS has no GitHub credentials), preview on port 3199, repoint `/opt/rocobroker-next/.next`, `pm2 restart rocobroker-next` (no `--update-env`). Full steps and rollback: `currentstate.md` in roco-w.

```sh

```

## Notes

- 

## Log

- 2026-10-25: Added
- 2026-10-26: GA4 tracking regression found by [[Roco SEO]]: rocobroker.com sessions in GA4 property 477009914 fell from ~50–120/day to ~1/day on 2026-09-13, and the live /fa HTML and script bundles load no gtag/GTM tag. Restore the tag; lost days cannot be backfilled. PageSpeed homepage also dropped from mobile 0.96 / desktop 1.00 (2026-10-15) to 0.34 (LCP 29.6 s) / 0.58 (2026-10-26). Single sample, needs a re-check.
- 2026-10-26: Deployed `b228752` (GA4 after analytics consent) as `/opt/rocobroker-releases/ga4-b228752`; rollback target `seo-audit-b0346f0`. Recovered unpushed production commits 5a017fd/3dd691e/b0346f0 into git `main` first, which was behind the live site. Accept analytics in the cookie banner to confirm GA4 realtime hits.
- 2026-10-26: Deployed `7d4b758` (SEO crawl fixes: blog H1 and server-rendered listing, shorter titles, sitemap, fixed links) as `/opt/rocobroker-releases/seo-7d4b758`; rollback target `ga4-b228752`. Article pages are prerendered from posts.json at build time; the database is used only after an admin publish. Admin edits still pending, listed in roco-w docs/seo-crawl-2026-10-26-content-edits.md.
- 2026-10-26: Deployed `0fe2b24`: MT5 Windows download temporarily redirects to a fixed pre-signed link that expires 2026-11-02 12:12 UTC. Revert to per-request signing before then. Rollback target `seo-7d4b758`.
