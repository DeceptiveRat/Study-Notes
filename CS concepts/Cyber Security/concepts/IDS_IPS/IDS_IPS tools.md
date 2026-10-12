1. Security Onion
- pros:
   - open-source Linux distribution
   - integrates a number of popular IDS tools
   - examines host log files and network traffic
   - can perform live network traffic analysis and store packets to file
- cons:
   - overlapping standalone tools
   - no action automation
   - some interfaces are not user-friendly

2. Snort
- pros:
   - free and open source
   - large library of pre-built detection rule
   - sniffer, packet logger, ID function
   - supported by Cisco
- cons:
   - unstable updates
   - reliant upon community support
   - highly complex with steep learning curve

3. Suricata
- pros:
   - free and open source
   - data collection at application layer
   - can monitor multiple protocols
   - integration with third-party tools
   - Lua scripting support
   - user-friendly interface
   - parallel processing with GPU support
- cons:
   - smaller support community
   - processor heavy

4. zeek
- pros:
   - open source
   - integrated traffic logging
   - tasks enable customized automation
   - monitor SNMP traffic and track FTP, DNS, and HTTP activity
- cons:
   - steep learning curve; requires SIEM and IDS knowledge
   - free open source version doesn't come with support
   - not available for Windows

5. Palo Alto Networks
- pros:
   - constantly updated threat protection profiles
   - blocks harmful sites
   - multiple defensive layers
   - blocks malformed packets, TCP reassembly, IP fragmentation, and C2 attacks
   - can deploy Suricata and Snort rules
   - cloud-native option
   - can scan encrypted traffic
- cons:
   - more expensive
   - lacks visibility into file analysis details
   - overly complex implementation steps

reference
- clearnetwork - IDS/IPS: <https://clearnetwork.com/top-intrusion-detection-and-prevention-systems/>