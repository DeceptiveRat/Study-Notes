1. trust
- provides security across multiple domains/forests
- authentication and resource access is allowed for trusted domains

2. transitive and non-transitive trusts
- determines whether trust can be extended outside of the two domains with which it was formed
- transitive: can extend trust relationships with other domains (implied, indirect trust)
- non-transitive: can deny trust relationships with other domains

3. trust relationship types
- parent-child:
   - automatically created when child domain is added
   - two-way, transitive
- tree-root:
   - automatically established between roots of two domain trees in same forest
   - two-way, transitive
- external trust:
   - manually created between domains in different forests or between AD domain and non-AD domain
   - one-way or two-way, non-transitive
   - used for resource sharing across forests
- forest trust:
   - manually created between root domains of two forests
   - transitive within each forest, but not across multiple forests => forests must connect directly, not indirectly
- shortcut trust:
   - manually created within forest to reduce authentication time between two domains
   - one-way or two-way, transitive
- realm trust:
   - establish connection between Windows domain and Kerberos realm
   - one-way or two-way, transitive or non-transitive
   - enables security integration between AD and UNIX/Linux environments
- cross-link trust:
   - created manually to improve authentication time between domains in different trees within same forest
   - transitive
   - used when authentication needs to bypass parent-child trust paths for efficiency

reference:
- Microsoft - AD concept trust: <https://learn.microsoft.com/en-us/entra/identity/domain-services/concepts-forest-trust>
- jumpcloud - AD trust: <https://jumpcloud.com/blog/active-directory-domain-trust-relationship-guide>