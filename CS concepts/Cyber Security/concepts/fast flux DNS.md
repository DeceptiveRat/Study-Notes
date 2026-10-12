## 1. Definition
rapid change of IP address associated with a domain name => difficult to track malicious infrastructure

### 1.1. single flux
domain name resolves to multiple IP address that change 

### 1.2. double flux
name server's IP address changes dynamically as well

## 2. How
- domain name mapped to multiple IP addresses of bots
- short TTL; frequent record update

## 3. detection and mitigation
- find domains with frequently changing IP addresses or low TTL values
- block known fast flux domains

reference (all):
chatGPT:
- <https://www.cloudflare.com/en-gb/learning/dns/dns-fast-flux/>
- <https://unit42.paloaltonetworks.com/fast-flux-101/>