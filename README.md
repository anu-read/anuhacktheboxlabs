# HTB Writeups

Documenting my progress through Hack The Box, starting with the **Starting Point** track.

> ⚠️ Note: I only publish writeups for **retired** machines. Active machines are excluded per HTB's terms.

## Progress

| Machine | Difficulty | OS | Topic | Writeup |
|---|---|---|---|---|
| Meow | Very Easy | Linux | Telnet default creds | [Link](machines/meow/README.md) |
| Fawn | Very Easy | Linux | Anonymous FTP | [Link](machines/fawn/README.md) |
| Dancing | Very Easy | Windows | Unauthenticated SMB | [Link](machines/dancing/README.md) |
| Redeemer | Very Easy | Linux | Unauthenticated Redis | [Link](machines/redeemer/README.md) |
| Reactor | Easy | Linux | Web app RCE → root via Node debugger | [Link](machines/reactor/README.md) |
| Cap | Easy | Linux | IDOR → credential leak → capability misconfig | [Link](machines/cap/README.md) |
| Management | Medium | Linux | Auth bypass → pre-auth RCE → sudo argument injection | [Link](machines/management/README.md) |

## Skills so far
- Basic enumeration with `nmap`
- Interacting with FTP, SMB, Telnet, Redis, and web services
- Spotting IDORs and analyzing traffic with Wireshark and Burp Suite
- Reading service banners and default configs for misconfigurations
- Virtual host discovery and HTTP header-based auth bypasses
- Chaining public CVEs into working exploits
- Linux privilege escalation via capabilities, exposed debug ports, and sudo misconfigurations
- HTB VPN setup and lab workflow

## About me
I'm learning offensive security from the ground up, working through HTB's Starting Point track and building this repo as I go. Connect with me on [LinkedIn](https://www.linkedin.com/in/ridwan-akande) / [X](https://x.com/mr___mob).