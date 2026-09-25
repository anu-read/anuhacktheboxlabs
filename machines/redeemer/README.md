# Redeemer — Very Easy (Linux)

**Category:** Redis
**Summary:** Enumerating and dumping data from an exposed, unauthenticated Redis server using `redis-cli`.

## Recon
```
# nmap -p- -sV <target-ip>

PORT STATE SERVICE VERSION
6379/tcp open redis Redis key-value store 5.0.7
```
Only one port open — Redis, with no other services to fall back on. That made it the obvious target.

## Enumeration
```
# redis-cli -h <target-ip>
<target-ip>:6379> info
```
The server accepted a connection with no authentication at all. Running `info` confirmed the version and showed one logical database (index `0`) under the Keyspace stats.

## Exploitation
```
<target-ip>:6379> select 0
<target-ip>:6379> keys *
<target-ip>:6379> get flag
```
- Selected database 0, then listed all stored keys with `keys *`.
- One of the keys was literally named `flag`; a few others (unrelated values) were also present.
- Ran `get` against the `flag` key to retrieve its value directly.

## Flag
Retrieved the flag value directly from the `flag` key in the Redis database (not reproducing the value here).

## Lessons learned
- Redis has **no authentication enabled by default** — anyone who can reach the port can read and write the entire dataset unless it's explicitly configured with a password (`requirepass`) and firewalled off.
- Worth always running `keys *` immediately after connecting to any exposed Redis instance — sensitive data is often stored under an obvious key name.
- In a real environment, Redis should never be exposed to untrusted networks; it should sit behind a firewall/VPC and have `requirepass` set at minimum.