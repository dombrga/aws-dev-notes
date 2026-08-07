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
   - ![org-archi](./images/31/org-archi.png)
4. **exam pro tip**: **aws iam identity center** (SSO) commonly integrates with aws organizations.
5. **aws:PrincipalOrgID** condition
   - global condition key
   - becomes available once you create aws org.
   - can use this key in Service Control Policies, iam identity policies, resource policies

## important aws organizations features
1. 2 feature sets
   1. All features
   2. Consolidated billing
### consolidated billing
1. free feature allowing all member acct bills to merge to a single payer acct. So, one payment method only.
2. that is why management acct is also called payer acct.
3. allows for discount sharing.
4. usage discounts for aggregate/volume use of member discounts.
### All features
1. StackSets - aws org allows to easily deploy cf stacks across accounts and regions.
2. Delegated admins
   - you can delegate policy/service management to member accts.
3. OrganizationAccountAccessRole
   - iam role created in each acct
   - to be assumed when needed
4. cost allocations tags
5. service control policies (SCPs) - policies to restrict/allow acct actions

## best practices for aws Organizations
1. multi acct strategy prevents you from running into acct svc limits.
   - create new acct and reset quota
2. you can enable organiztaional cloudtrail trail for centralized logging.
3. implement logging/security acct for hosting centralized cw logs in s3.
