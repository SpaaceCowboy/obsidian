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
- 2026-10-26: Deployed `b80f7c0`: restored 160 missing inline blog images and imported 7 unmigrated Persian posts from wp.rocobroker.com. Rollback target `mt5-0fe2b24`. The database copies are not updated yet, so an admin republish of those articles would drop the images.
- 2026-10-26: Consent-gated GA4 tag (roco-w 0028a09) deployed and verified: GA4 Realtime shows rocobroker.com page views after analytics consent; nothing loads before consent.
- 2026-10-26: Content database synced with the restored WordPress media: 7 posts imported, and 160 images added to 58 articles as new revisions. Backup taken first (`/home/rocoweb/backups/wp-media-b80f7c0/`). An admin republish no longer drops the images.
