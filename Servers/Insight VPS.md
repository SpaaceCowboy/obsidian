---
type: server
provider: HostVDS
ip: 13.140.89.146
os: Ubuntu
cost: $4/mo
renews:
access: password manager → 
---
# Insight VPS

Runs the Insight game backend and APK download.

## Services on this server

```base
filters:
  and:
    - file.inFolder("Services")
    - file.hasLink(this.file)
views:
  - type: table
    name: Services
    order:
      - file.name
      - status
      - url
      - port
      - deployed
```

## Notes

- Android QA runs here through KVM, never on the user's local PC. SDK: /opt/android-sdk; Gradle cache: /opt/insight-gradle. Use isolated test data and stop the emulator after verification.

## Log

- 2026-10-25: Added
- 2026-10-26: Added a headless Android 8 KVM test device and moved release builds/tests onto the VPS to relieve local-PC pressure. Live Insight service remains healthy; test processes stopped after the release.
