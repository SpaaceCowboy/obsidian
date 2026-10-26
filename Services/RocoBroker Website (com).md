---
type: service
server: "[[Host1]]"
status: running
url: https://rocobroker.com
port:
deployed: 
repo: https://github.com/SpaaceCowboy/roco-w.git
---
# RocoBroker Website (com)

Main site. Project: [[RocoBroker Website]].

## How to deploy / update

```sh

```

## Notes

- 

## Log

- 2026-10-25: Added
- 2026-10-26: GA4 tracking regression found by [[Roco SEO]]: rocobroker.com sessions in GA4 property 477009914 fell from ~50–120/day to ~1/day on 2026-09-13, and the live /fa HTML and script bundles load no gtag/GTM tag. Restore the tag; lost days cannot be backfilled. PageSpeed homepage also dropped from mobile 0.96 / desktop 1.00 (2026-10-15) to 0.34 (LCP 29.6 s) / 0.58 (2026-10-26). Single sample, needs a re-check.
