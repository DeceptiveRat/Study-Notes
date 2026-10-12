1. identity and access management (IAM)
- make it easy to enforce multi-factor authentication 
- enable organizations to leverage conditional access policies (CAP)
- generate alerts about suspicious logon attempts and telemetry 
- but allows adversaries to target a centralized identity and gain access to numerous systems => should be monitored closely

2. methods for compromising identities
- phishing
- malware
- session hijacking
- vulnerability exploitation
- credential stuffing
- password spraying 
- data leaks
- adversary-in-the-middle, man-in-the-middle attacks
   - present users with fake login page
   - can bypass MFA
- MFA circumvention
   - methods include:
      - aitm/mitm attacks
      - MFA exhaustion
      - SIM swap
      - help desk social engineering

3. prevention
- MFA
- CAP
   - establishes perimeters around permissible logins
- passwordless solutions
   - includes hardware tokens, hardware-based authentication devices, and biometrics
   - can be challenging to implement at scale 
- short-term access