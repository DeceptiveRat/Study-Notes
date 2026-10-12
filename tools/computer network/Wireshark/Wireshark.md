# 1. Installation
sudo apt install wireshark

- running wireshark as root can be dangerous so it is recommended to allow not-root users to use it, if they are in the group wireshark
sudo dpkg-reconfigure wireshark-common
sudo adduser $USER wireshark

# 2. Usage
- protocols for finding hostname:
   - NBNS
   - SMB
   - kerberos: AS-REQ

- protocols for finding user account name:
   - kerberos: AS-REQ

- finding full name of user
   - ldap.AttributeDescription == "givenName"