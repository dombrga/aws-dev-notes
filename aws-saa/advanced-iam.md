## June 24, 2026

### aws directory services
1. to set up and run ms active directory with other aws svcs.
2. offload AD over to aws.
3. aws directory svcs options
   1. aws managed microsoft AD.
      - entire suite of AD created within aws.
      - for one-way or two-way trusts.
      - most amount of features.
      - best for >5000 users.
   2. whats trust?
      - oneway trust - domain trust another, not other way around.
      - twoway trust - domains at each end trust each other both ways.
   3. AD connector
      - gateway to redirect requests to onprem MS AD.
      - connects existing AD to aws.
      - best if you want to avoid data retention in aws.
      - small and large.
   4. simple AD
      - standaline managed directory.
      - small, large.
      - subset of features of aws managed AD.

### AWS IAM identity center
1. for connecting workforce users to aws accts and aws-managed apps.
2. provides single place to manage logins for an org.
3. can connect existing identity providers (ms ad, okta)
4. create and manage users.
5. use case
   1. grant user access to app hosted in aws.
   2. like #1, but to aws accounts in multi-acct orgs
6. compatible apps
   1. cloud apps like salesforce, ms365, confluence.
   2. saml-2.0 business apps.
   3. ec2 windows instances.
7. iam ic assignments and permissions
   1. assign user/aws accounts permission sets/policies to define level of access.
   2. application assignments.
   3. attribute-based access control (ABAC)
8. setup AWS Organization to use iam ic.

## June 25, 2026

### troubleshooting overlapping iam policies
1. permission evaluation order
   1. explicit deny
   2. service control policy
   3. resource-based policy
   4. identity-based policy
   5. permission boudnaries
   6. session policy
2. there is an implicit deny in AWS in any requests.
3. permission boundary
   - feature using managed policy to set maximum permissoin than an identity-based policy can grant to iam identity.
   - for example, you delegate iam to an admin, but you want to limit admin the maximum permission they can grant.
4. new IAM entities always start with zero permissions. There is implicit deny. Grant explicit access if needed.

### custom conditions and statements
1. condition statements
   1. externalID
      - unique identifier that cen be required when you assume a role in another account.
      - confused deputy problem.
   2. aws:MultiFactorAuthPresent
      - checks if user has authenticated with MFA.
   3. aws:SourceIp
      - restrict access based on requester IP addr.
   4. aws:PrincipalOrgID
      - validates that the request comes from an acct that is a member of specific aws org.