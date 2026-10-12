1. Zeek
- scriptable network traffic analyzer
- unlike traditional IDS (Snort, Suricata) provides context-rich logs
- better suited for forensics, threat hunting, and network security monitoring

2. Zeek architecture
- event engine:
   - analyzes network packets
   - raises events
- script interpreter:
   - scripts define actions to take when events are triggered
- clusters:
   - manager: combines logs and manages cluster
   - logger: collect and save log data
   - proxy: synchronization between worker nodes
   - worker: packet analysis

3. key frameworks
- file analysis:
   - extract and hash files from network traffic
- signature framework:
   - detect known patterns in payloads
- intel framework:
   - integrate threat intelligence feeds
- logging framework:
   - generate logs
- notice framework:
   - generate alerts

4. Zeek logs
- Tab-Separated Values (TSV)
- easy to analyze with CLI tools

5. Zeek common logs
- conn.log:
   - connection metadata
- dns.log
- http.log
- files.log
- notice.log
- intel.log:
   - threat intel
- signatures.log:
   - signature rule matches

reference:
- <https://medium.com/@ashutoshthakurofficial/deep-dive-into-zeek-a-powerful-network-security-monitoring-tool-f52ff3485035>