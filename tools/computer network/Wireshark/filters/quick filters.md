- search for traffic over TCP 80 and TCP 443 that aren't internal

```plain-text
tcp.flags eq 0x0002 and !(tcp.port eq 443) and !(tcp.port eq 80) and !(ip.dst eq 10.7.10.0/24)
```

- searching for duplicate use of IP

```plain-text
arp.duplicate-address-detected && arp.opcode == 2
```
