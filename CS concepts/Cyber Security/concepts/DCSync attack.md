1. DCSync attack
- typically used to steal credentials from AD database
- attacker impersonates Domain Controller (DC) using Directory Replication Services (DRS) Remote Protocol
- no need to run code on DC
- adept at bypassing detection
- permissions needed by attacker:
   - Replicate Directory Changes
   - Replicate Directory Changes All

source:
- semperis
<https://www.semperis.com/blog/dcsync-attack/>
