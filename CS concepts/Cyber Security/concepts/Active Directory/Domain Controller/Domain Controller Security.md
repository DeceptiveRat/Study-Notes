1. who can access DCs
- grant DC logon rights via GPO => should be restricted
- non-administrator users should not have access to DC

2. DC compromise
- stolen sensitive information such as credentials => potential compromise of other systems
- attacker controlled accounts with admin privileges
- malware spread across network
- ordinary operations disrupted

3. improving DC security
- verify tier 0 objects, such as Domain Admins group, contain only necessary users
- for GPOs linked to the DC OU ensure:
   - only Domain Admins have **Allow Log on Through Remote Desktop Services** right
   - only Domain Admins have **Allow Log On Locally** right

reference:
- semperis - AD security: <https://www.semperis.com/blog/ad-security-101-domain-controller-security/>