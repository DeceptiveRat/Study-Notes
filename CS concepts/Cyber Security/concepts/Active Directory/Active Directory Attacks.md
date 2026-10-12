1. Kerberoasting
- obtain service ticket and perform password cracking to obtain credentials for that service
- requires compromised user to get service ticket
- prevention:
   - limit number of accounts with SPNs
   - disable dead accounts
   - ensure strong passwords
   - Group Managed Service Accounts (GMSA)
      - particular service account that AD manages
      - bound to a specific server
      - password is automatically rotated
      - not all applications support this

2. AS-REProasting
- extract hashes for accounts with pre-authentication disabled
- crack hash to obtain user credentials
- doesn't require compromised user
- prevention:
   - limit users without pre-authentication disabled
   - separate password policy for users with Kerberos pre-authentication disabled

3. Group Policy Preferences (GPP) passwords
- AD stores credentials in the policies directory in SYSVOL
- attacker can parse XML files in policies directory to obtain credentials
- prevention:
   - patch to prevent caching of credentials
   - continuous assessment to make sure no credentials are exposed

4. Group Policy Object (GPO) misconfiguration
- compromised users can edit GPO
- prevention:
   - never deploy files stored in network locations so users can modify share permissions
   - regularly review GPO permissions

5. DCSync
- attacker impersonates DC to request password hashes from target DC, using directory replication
- attacker must first gain access to account with high-level permissions:
   - Replicating Directory Changes
   - Replicating Directory Changes All
- prevention:
   - block or allow specific RPC calls to block replication requests

6. golden ticket
- can generate tickets for any user in domain
- requires password hash of krbtgt
- prevention:
   - block privileged users from authenticating to any device
   - periodically reset krbtgt password

7. Kerberos constrained delegation
- a service(A) account is compromised
- authenticated it to KDC for user(B) to impersonate
- KDC returns service ticket for B to use A
- if A is trusted for constrained delegation the service ticket returned can be used to impersonate B to services to which delegation is allowed

reference:
- htb academy