When analyzing captured packets from a device you suspect is infected, you're essentially hunting for signs of **command-and-control (C2) communication**, **data exfiltration**, **scanning or lateral movement**, and **unusual behavior**. Here's what to look for, broken down into categories:

---

### 🔍 **1. Unusual Destinations**

* **External IPs** in countries you don't expect communication with.
* Connections to **known malicious IPs or domains** (check against threat intelligence feeds like VirusTotal, AbuseIPDB, etc.).
* **Dynamic DNS services** (e.g., `no-ip.org`, `duckdns.org`), often used for C2.

---

### 📦 **2. Suspicious Protocols or Traffic Types**

* **Non-standard ports** (e.g., SSH on port 8888, HTTP on port 8081).
* **Cleartext protocols** like FTP, Telnet, or HTTP when you'd expect encryption.
* **Unexpected protocols** (e.g., SMB traffic to the internet, IRC).

---

### 🕒 **3. Timing and Patterns**

* **Beacons**: Regular outbound connections (e.g., every 10 seconds/minute/hour)—indicates C2 beaconing.
* **Long durations** or **large volumes** of outbound traffic could suggest data exfiltration.

---

### 🧾 **4. Payload Contents**

* In unencrypted packets, look for:

  * **Suspicious strings** (e.g., base64 blobs, PowerShell commands, encoded binaries).
  * Credentials or internal file names.
* In encrypted traffic (like TLS), inspect:

  * **SNI fields** for odd domain names.
  * **Certificates** used—self-signed or invalid certs can be indicators.

---

### 🔄 **5. DNS Requests**

* High frequency of DNS queries to **unusual or algorithmically generated domains (DGA)**.
* Queries for **suspicious TLDs** (`.xyz`, `.top`, `.club`, etc.).
* **TXT record usage**—sometimes used for C2.

---

### 🧑‍💻 **6. Behavioral Anomalies**

* Device making **connections during off-hours** (e.g., midnight to 4am).
* Internal IP making **port scans** or communicating with many devices unusually fast (indicative of worm-like behavior or lateral movement).
* Use of **proxy or VPN services** that weren't previously seen.

---

### ⚠️ **7. Known Indicators of Compromise (IOCs)**

* IPs, domains, file hashes, or URLs linked to malware/C2.
* You can compare against open source threat intel feeds like:

  * AlienVault OTX
  * AbuseIPDB
  * IBM X-Force Exchange

---

Would you like a workflow or toolset suggestion for how to go about this packet analysis (e.g., using Wireshark, Zeek, Suricata, etc.)?
