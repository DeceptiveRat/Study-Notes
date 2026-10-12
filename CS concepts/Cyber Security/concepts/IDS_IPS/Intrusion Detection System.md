1. Intrusion Detection System (IDS)
- network security tool
- monitors network traffic for known malicious activity
- certain regulations require organizations to implement IDS - [1]
- integrated with Intrusion Prevention System (IPS)

2. signature-based detection
- analyzes network packets for attack signatures
- maintains database of attack signatures
- weak against new attacks with unknown signatures

3. anomaly-based detection
- use machine learning to create model of normal activity
- flag deviations from normal activity
- can catch new cyberattacks
- more prone to false positives

4. other detection methods
- reputation-based detection:
   - blocks traffic from IPs and domains associated with malicious activity
- stateful protocol analysis:
   - focuses on protocol behavior

5. IDS types
- Network Intrusion Detection System (NIDS):
   - monitor inbound and outbound traffic across network
   - placed in strategic points in network (e.g. immediately behind firewalls)
   - can be placed in network to catch insider threats or compromised accounts
   - usually placed out-of-band, i.e. analyzes copies of packets
- Host Intrusion Detection System (HIDS):
   - installed on specific endpoint
   - typically works by taking periodic snapshots of critical operating system files and comparing over time
- Protocol-based IDS (PIDS):
   - monitors connection protocols between servers and devices
   - often placed on webservers to monitor HTTP/HTTPS connections
- Application protocol-based IDS (APIDS):
   - monitors application protocols
   - often deployed between web server and SQL database to detect SQL injections
- Virtual machine-based IDS (VMIDS):
   - detects intrusions by monitoring VMs

6. IDS evasion tactics
- Distributed denial-of-service (DDos) attacks:
   - take IDSs offline with malicious traffic from multiple sources
- Spoofing:
   - fake IP addresses and DNS records to make traffic look like it's from legitimate sources
- Fragmentation:
   - split payload into small packets to avoid detection
   - can also send out of order
- Encryption
- operator fatigue:
   - large number of IDS alerts can distract operators

7. integration with other solutions
- IDS and SIEM:
   - IDS alerts are funneled into SIEM
   - SIEM combines and enriches alerts
   - easier to filter out false positives
- IDS and IPS:
   - IPS can also terminate malicious connections
   - IPS is placed inline
   - most companies deploy together as IDPS
- IDS and firewalls:
   - firewalls act as barriers to block traffic
   - IDS catches what slipped through
   - some next-gen firewalls have built-in IDS and IPS functions

reference:
- IBM - IDS: <https://www.ibm.com/think/topics/intrusion-detection-system>
- Fortinet - IDS: <https://www.fortinet.com/resources/cyberglossary/intrusion-detection-system>

notes:
[1]: such as Payment Card Industry Data Security Standard (PCI-DSS)