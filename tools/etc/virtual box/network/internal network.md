set static IP
- windows: control panel => Network and Internet => Network and Sharing Center => Change Adapter Settings => right click ethernet => properties => Internet Protocol Version 4 (TCP/IPv4) Properties
- linux: sudo ifconfig enp0s3 192.168.56.101 netmask 255.255.255.0 up