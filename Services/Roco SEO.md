---
type: service
server: "[[Crawler VPS]]"
status: running
url: https://scc.rocobroker.com
port:
deployed: 
repo: https://github.com/SpaaceCowboy/seo-automation
---
# Roco SEO

SEO Control Center. Project: [[SEO Automation Ecosystem]].

## How to deploy / update

```sh

```

## Notes

- 

## Log

- 2026-10-25: Added
- 2026-10-26: Deployment attempt stopped before any server changes. Existing-key SSH to the documented server returned Permission denied (publickey). Local changes were pushed as d72e4c1 on codex/phase4-opportunity-engine; this older branch must be reconciled with main before deployment because migration histories differ. Exact running server revision remains unverified. See [[SEO Automation Ecosystem]].
- 2026-10-26: SSH access now verified with the local roco_deploy_v2 key via ssh-agent. API readiness HTTP 200 confirms database and queue ready; API image roco-seo:staff-ga4-host-20261015, worker roco-seo:worker-agent-schema-20261016 and dashboard roco-seo:staff-ui-414a4e1 are healthy. Live opportunity tables match the newer schema rather than the alternate Phase 4 branch. No services restarted, migrations applied or deployment performed. Other hosted applications were left untouched; authenticated dashboard workflows remain unverified.
