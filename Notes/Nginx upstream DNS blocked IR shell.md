---
type: note
tags: [fix]
service: "[[RocoBroker Website (ir)]]"
---
# Nginx upstream DNS blocked IR shell

## Error

```text
host not found in upstream "rocobroker.com" in /etc/nginx/snippets/rocobroker-ir-locations.conf:7
```

## Cause

- On 2026-10-24, Nginx failed its startup configuration check when the optional .com relay hostname could not resolve. Ports 80/443 stayed closed although the standalone app on [[Roco VPS]] was healthy at 127.0.0.1:3100.

## Fix

Use request-time DNS for the fixed public relay hostname in both form and MT5 download locations:

```nginx
resolver 127.0.0.53 ipv6=off valid=300s;
resolver_timeout 5s;
set $roco_public_host rocobroker.com;
# Inside the existing relay locations:
proxy_pass https://$roco_public_host$request_uri;
```

Keep the existing HTTPS SNI/certificate checks, origin validation and sanitized headers. After validating the configuration, start Nginx; future DNS failures affect relay requests rather than the entire marketing shell.

```sh
nginx -t && systemctl reload-or-restart nginx
bash /opt/rocobroker-ir/current/deploy/verify-rocobroker-ir-dns.sh
cd /opt/rocobroker-ir/current
node scripts/verify-shell.mjs https://rocobroker.ir
```

## Verify

- Isolated Nginx starts with unavailable upstream DNS; contact/lead relays return 502 while marketing pages return 200.
- Six-language HTTPS, assets, canonicals, exclusions, form relays and MT5 checks passed.
- Nginx and app active; certificate expires 2027-01-20 and renewal timer active. No .com changes or real form submissions.

Fixed on 2026-10-26

## Log

- 2026-10-26: Diagnosed the two-day proxy outage, restored Nginx and deployed/tested the runtime-DNS fix. Related project: [[RocoBroker Website]].
