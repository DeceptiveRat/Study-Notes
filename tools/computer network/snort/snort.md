## 1. common options
- -A: alert mode
   - fast
   - full (default)
   - none
   - unsock
   - console (fast + display to console)
- -r: read pcap
- -i: interface
- -l: log location
- -c: configuration file
- -q: quiet mode
- -Q: inline mode (requires proper DAQ and 2 interfaces)
sudo snort -q -A console -i enp0s3:enp0s8 -c /etc/snort/snort.conf --daq afpacket -Q