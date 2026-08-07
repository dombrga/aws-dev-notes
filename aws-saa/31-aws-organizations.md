## multi-account archi
1. critical design strategy based on well-architected framework
2. example acct structure
   1. acct per environment
   2. acct per department (hr, billing, security)
3. benefits
   1. stricter controls for security and compliance.
   2. isolate workloads and reduce blast radius.
   3. billing separation
4. how to manage multiple accts at scale? **AWS Organizations**!

# aws Organizations
1. free governance tool to create and manage multiple aws accts in single loc.
2. When you create an organization, you get one main acct called **management account**, aka **payer account**.
   - other accts that are created/join the org are called **member accts**.
   - member accts only belong to single org.
   - logically group member accts using **Organizational Unit (OU)**
3. aws organizations high level archi
   - Root OU - default ou, always available.
4. **exam pro tip**: **aws iam identity center** (SSO) commonly integrates with aws organizations.
5. **aws:PrincipalOrgID** condition
   - global condition key
   - becomes available once you create aws org.
   - can use this key in Service Control Policies, iam identity policies, resource policies
   - **exam scenario** -