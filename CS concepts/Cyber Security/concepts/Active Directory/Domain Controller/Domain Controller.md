1. Domain Controller (DC)
- server that responds to security authentication requests
- can be used with identity management systems other than AD
- runs Active Directory Domain Services (AD DS) role
- functions:
   - authenticate users
   - control access to domain resources
   - apply security policies
   - KDC for Kerberos authentication
- usually implemented in clusters => improved reliability/availability
- hosts copy of the directory
- replicates updates to other DCs in domain/forest

2. Domain Controller and security
- compromising a DC allows access to all data stored on network
- DCs are the primary target for attacks
- additional security mechanisms should be used:
   - firewalls
   - isolated networks
   - encryption for stored data and data in transit
   - restricted use of insecure protocols (e.g. Remote Desktop Protocol)
   - deployment in physically secure location
   - expedited patch and configuration management
   - blocked internet access
   - dedicated administrator accounts

3. Domain Controller benefits
- centralized management of authentication
- enforcement of security policies
- seamless integration with Microsoft AD

4. Domain Controller limitations
- single point of failure for network domain control
- target for attacks
- requires additional security infrastructure

reference:
- TechTarget - domain controller: <https://www.techtarget.com/searchwindowsserver/definition/domain-controller>