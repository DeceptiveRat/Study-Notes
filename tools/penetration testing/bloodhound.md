# 1. installation
sudo pip install bloodhound

# 2. usage
## (1) starting bloodhound
- neo4j console is required to run bloodhound
sudo neo4j console

- use the interface for neo4j
- run sudo bloodhound
- login to neo4j database using the username and password

## (2) Collecting information
- usage: sudo bloodhound-python -d <domain> -u <user> -p <password> -ns <namespace> -c <collecting>
- example: sudo bloodhound-python -d MARVEL.local -u fcastle -p Password1 -ns 192.168.138.136 -c all
this saves data to the directory that the command was run in

- you can upload the data to the bloodhound browser

---
reference:
(1) tcm-sec: [Domain Enumeration with Bloodhound](<wazuh components.md>)