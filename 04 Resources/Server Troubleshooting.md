# Server Troubleshooting

#resource #server #technical-fix

## Purpose

Provide a repeatable path for diagnosing server incidents without losing evidence or making untracked changes.

## Initial triage

- [ ] Record start time, affected service, user impact, and correlation/incident ID
- [ ] Check resource pressure, failed units, recent deploys, and dependency health
- [ ] Confirm the symptom from outside the host where possible
- [ ] Preserve relevant logs without copying credentials or PII

## Diagnostic checklist

### Service

- Status and restart history: 
- Recent logs: 
- Configuration changes: 

### Host

- CPU/memory/disk: 
- Time synchronization: 
- Network/listeners/firewall: 

### Dependencies

- Database/Redis/queue: 
- DNS/TLS: 
- External vendor: 

## Resolution and verification

- Fix applied: 
- Expected outcome verified: 
- Monitoring/reconciliation verified: 
- Rollback available: 

## Related notes

- [[Debian Commands]]
- [[IT Infrastructure]]
- [[Server & Infrastructure MOC]]
- [[07 Templates/Technical Fix Template|Technical Fix Template]]
