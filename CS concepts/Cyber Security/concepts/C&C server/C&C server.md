## 1. What is a C2(C&C) server?
A command-and-control (C&C) server is a computer controlled by an attacker that is used to:
- send commands
- receive stolen data

reference (1.):
<https://www.trendmicro.com/vinfo/us/security/definition/command-and-control-server>

## 2. How are C&C servers used?
A C&C server may be used to carry out:
- data theft
- reboot devices
- network shutdown
- DDoS attacks
- Advanced Persistent Threat (APT)
- botnet

### 2.1. C&C server case study 1: Emotet
(view in case studies node)

reference (2.):
<https://www.techtarget.com/whatis/definition/command-and-control-server-CC-server>

further reading (2.):
<https://securelist.com/server-side-attacks-cc-in-public-clouds-mdr-cases/107826/>

## 3. How do C&C servers hide their IP address?
### 3.1. fast flux DNS
(view in concepts node)

### 3.2. onion routing
Tor's hidden services

further reading (3.2.):
<https://ieeexplore.ieee.org/document/6916408>

### 3.3. VPN

### 3.4. P2P

### 3.5. cloud
cloud services can be used to host C&C servers

further reading (3.5.):
<https://www.security.com/threat-intelligence/cloud-espionage-attacks>

### 3.6. CDN
domain fronting can be used to mask C&C traffic

reference (3.6.):
<https://www.cyberark.com/resources/threat-research-blog/implementing-malware-command-and-control-using-major-cdns-and-high-traffic-domains>