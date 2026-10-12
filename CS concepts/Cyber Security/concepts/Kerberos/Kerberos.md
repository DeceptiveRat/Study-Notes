1. Kerberos
- authentication protocol
- allows nodes to prove their identities over insecure channel

2. Key Distribution Center (KDC)
- Authentication Service (AS)
   - provides authentication
- Ticket Granting Service (TGS)
   - grants service ticket

3. Ticket Granting Ticket (TGT)
- special ticket issued by AS
- acts as proof of authentication
- allows requesting service tickets
- encrypted with KDC's krbtgt account key => non-modifiable by client

4. Kerberos authentication steps (simple)
- step 1. request TGT
   - log in with password/NT hash
   - KDC gives TGT
- step 2. request service ticket
   - with TGT it's possible to get service ticket for any service
- step 3. access attempt
   - present service ticket to service
   - service decrypts ticket with service account's key
   - if authorized, access is granted