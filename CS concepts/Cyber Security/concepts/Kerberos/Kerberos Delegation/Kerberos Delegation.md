1. kerberos delegation steps
- user authenticates to KDC and receives TGT
- when accessing service that requires delegation, service requests service ticket on behalf of the user
- KDC issues service ticket that initial service can use to request access to downstream service
=> ensures user credentials are never exposed to services

2. types
- unconstrained delegation
- constrained delegation
- resource-based constrained delegation

3. unconstrained delegation
- service can request access to any other service
- significant security risk if not managed => suitable for trusted environments
- authentication flow:
   - user requests TGS for service A from KDC
   - KDC includes user's TGT in TGS for service A if service A is trusted for delegation
   - user authenticates using TGS
   - service A requests TGS for service B from KDC using TGT of user
   - KDC sees valid TGT and issues TGS for service B
* service has TGT of user in memory *

4.  constrained delegation
- specify in advance services allowed for delegation
- relies on Service for User to Proxy (S4U2Proxy) extension
- authentication flow:
   - user requests TGS for service A from KDC
   - user authenticates using TGS
   - service A uses S4U2Proxy to request TGS for service B on behalf of user
   - if service A is allowed to delegate to service B, KDC issues TGS for service B with user's identity

5. resource-based constrained delegation
- service admin controls which services can delegate to it

reference:
- silverfort - kerberos delegation: <https://www.silverfort.com/glossary/kerberos-delegation/>
- medium - kerberos delegation: <https://medium.com/r3d-buck3t/attacking-kerberos-constrained-delegations-4a0eddc5bb13>