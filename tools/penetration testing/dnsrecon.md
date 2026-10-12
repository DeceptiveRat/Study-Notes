# 1. installation
sudo apt install dnsrecon
# 2. usage

```sh
dnsrecon -r <local host>/24 -n <target ip> -d <domain>
```


-r: range
-d: domain

- eg.

```sh
dnsrecon -r 127.0.0.0/24 -n 192.168.0.64 -d xxx
```
(1)

---
(1)
Q. Why use the range for the attacking machine?
A.
### 1. **Why Use `127.0.0.0/24`?**

The `127.0.0.0/24` range refers to loopback addresses, commonly used for the localhost (`127.0.0.1`). It may seem odd to scan this range when the target is in a different address space (like `192.168.x.x`). However, there is likely a reason related to **reverse DNS (PTR records)**.

#### Reverse DNS Lookups:
- When using `dnsrecon` with the `-r` option (for a reverse DNS scan), you are scanning for PTR records, which map IP addresses to domain names (the reverse of what A records do).
- If you're scanning a loopback address range (`127.0.0.0/24`), you're specifically looking for PTR records related to loopback addresses. These are often used internally, and in certain network configurations, you might still find useful results.

In this context, you might be looking for PTR records that relate to **how internal hostnames (like `blackpearl.tcm`) are mapped to IPs**, even if the target is external. It's possible that this setup uses loopback addresses for internal DNS resolution purposes, which might explain why you're using `127.0.0.0/24` for the reverse lookup.

However, if the target network is entirely different, you would typically scan the range that corresponds to the target network (e.g., `192.168.0.0/24`). If `127.0.0.0/24` isn't giving useful results, it could be worth testing the actual target network range.

Q. What does the flag -n do?
A. 
### 1. **The Purpose of the `-n` Flag**

The `-n` flag in `dnsrecon` specifies the **name server (DNS server)** that will be used for DNS queries during the scan. When performing DNS lookups or reverse DNS lookups, `dnsrecon` needs to query a DNS server, and the `-n` option lets you specify which server to use.

Here’s why this is important:

- **Choosing the Right DNS Server**: Different DNS servers may provide different responses, especially if the target network uses **internal DNS servers** for private records or internal configurations. If you query a public DNS server, it may not have access to internal DNS information, and you may miss important details.
- **Bypassing the Default DNS Server**: By default, `dnsrecon` will use the DNS server configured on your system (usually from your network or ISP). The `-n` flag lets you override this and specify the exact DNS server you want to query.

For example:

```sh
dnsrecon -r 127.0.0.0/24 -n 192.168.0.64 -d example.com
```


In this command:
- You're scanning for PTR records in the `127.0.0.0/24` range.
- You're telling `dnsrecon` to use `192.168.0.64` as the DNS server to perform the lookup, instead of the default system DNS.

### When You Might Use `-n`:
- If the target network has **internal DNS servers** not exposed to the public.
- When you want to query a specific DNS server (e.g., one closer to the target network) to get more accurate or complete DNS records.
- If you're testing DNS configurations and need to ensure you're querying a specific server that holds the relevant records.

### Example Scenarios:
- You might specify `-n` to point to an **internal DNS server** when targeting an internal network, as this DNS server would know more about internal hosts (including private PTR records).
- For external DNS testing, you could use a **public DNS server** (like `8.8.8.8`) to check how records appear outside the target network.