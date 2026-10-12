# (1) Answers section
## 1. Query name
- domain name
- variable length

## 2. type
- DNS record type
- 2 bytes

## 3. class
- data class
- 2 bytes

## 4. TTL
- time to live
- 4 bytes
- number of seconds to be cached

## 5. Data length
- 2 bytes
- specifies octet count in the resource data field

## 6. Resource data
- variable length
- answer to the query

# (2) Authoritative Name Servers
same fields as answers section

# (3) Additional records
same fields as answer section


---
reference:
(1): <https://www.firewall.cx/networking/network-protocols/dns-protocol/protocols-dns-response.html>