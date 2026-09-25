# Meow — Very Easy (Linux)

**Category:** Introductory / Telnet
**Summary:** An introductory box used to practice basic HTB workflow — connecting via VPN, scanning, and exploiting a Telnet service left open with default credentials.

## Recon
```
# sudo nmap -sV <target-ip>

PORT STATE SERVICE VERSION
23/tcp open telnet Linux telnetd
```

## Enumeration
- Only one open port: 23 (Telnet) — an old, unencrypted remote login protocol.
- Since Telnet often ships misconfigured on intentionally vulnerable boxes, tried logging in with a common default username before doing anything else.

## Exploitation
```
# telnet <target-ip>
login: root
```
Logged straight in as `root` with no password required at all — dropped directly into a root shell.

## Flag
*Captured the flag from `flag.txt` found directly in the root's home directory after login (not reproducing the flag value here).*

## Lessons learned
- Telnet transmits everything in plaintext and, here, didn't even enforce a password for `root` — a reminder of why Telnet is considered obsolete and dangerous on any real network.
- Always worth trying the most obvious default credentials first on legacy services before diving into deeper enumeration.