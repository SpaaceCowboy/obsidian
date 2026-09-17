# Debian Commands

#resource #server

## Purpose

Keep reviewed Debian commands and short operational recipes with enough context to use them safely.

## System information

```sh
uname -a
cat /etc/os-release
systemctl --failed
```

## Services and logs

```sh
systemctl status SERVICE
journalctl -u SERVICE --since today
```

## Networking

```sh
ss -ltnp
ip address
ip route
```

## Packages

```sh
apt list --upgradable
```

## Caution notes

- Replace placeholders before running commands.
- Record destructive or production-changing procedures in a dedicated runbook.
- Capture expected output and verification, not secrets or sensitive log bodies.

## Related notes

- [[Server & Infrastructure MOC]]
- [[IT Infrastructure]]
- [[Server Troubleshooting]]
