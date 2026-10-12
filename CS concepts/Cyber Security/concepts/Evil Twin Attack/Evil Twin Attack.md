1. Evil Twin Attack
- users connect to fake wifi Access Point (AP) set up by attacker 
- all traffic is exposed to attacker

2. Evil Twin Attack process
- set up fake AP:
   - set up new account with same SSID as legitimate ones
   - used devices:
      - smartphone
      - laptop
      - tablet
      - portable routers
   - device must have 2 Internet cards; one for association with LAP and another for impersonation of LAP
- lure victims:
   - use strong signals to get devices to connect
- set up fake captive portal:
   - victims disclose login credentials to fake site
   - the credentials are used to login to the legitimate network

3. protecting against Evil Twin Attack
- avoid unsecured wifi hotspots
- use personal hotspot
- check warning notifications
- disable auto-connect
- avoid logging into private accounts on public wifi
- use Multi Factor Authentication (MFA)
- stick to HTTPS websites
- use VPN

4. types
- passive method:
   - use signal strength to get victims to connect to fake AP
- active method:
   - launch deauthentication attack to disconnect victims from Legitimate AP (LAP) and connect them to fake AP

reference:
- kaspersky - Evil Twin Attack: <https://www.kaspersky.com/resource-center/preemptive-safety/evil-twin-attacks>
- IEEE - Overview On Public Wi-Fi Security Threat Evil Twin Attack Detection: <https://ieeexplore.ieee.org/document/9398377>
S. A. A. Ahadi, N. rakesh and S. varshney, "Overview On Public Wi-Fi Security Threat Evil Twin Attack Detection," 2020 IEEE International Conference on Advent Trends in Multidisciplinary Research and Innovation (ICATMRI), Buldhana, India, 2020, pp. 1-6, doi: 10.1109/ICATMRI51801.2020.9398377. keywords: {Technological innovation;Machine learning;Market research;Hardware;Security;IP networks;Wireless fidelity;Evil Twin;LAP;SSID;Wi-Fi Security;RTT;External IP address;ETAD;IDS;ML},