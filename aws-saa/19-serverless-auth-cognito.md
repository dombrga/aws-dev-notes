## Amazon Cognito
1. aws-native, serverless identity provider.
2. offers authentication, authorization, user mgmnt.
3. easily integrates with web and mobile app without needing custom code.
4. username password or 3rd party like fb, google, etc.
5. mobile user sign ups and auth.
6. Cognito pools
   1. User pools
   2. Identity pools

## cognito user pool
1. directory of user that provide register/signin opts for app users.
2. Authenticated users are provided with JWT.
3. authn options incliude basic auth, federated 3rd party IdP like fb, google.
4. allow to require mfa, reset their own pass, require email or phone verif.
5. Adaptive authn - block suspicious sign-ins or add another second factor authn.
6. some architecture
   1. Cognito user pools can be used as api gw authorizers.
   2. ALB can have an **authenticate-cognito** action configured to offload authn workloads to ALB instead of your app.

## cognito identity pool
1. give your users access to aws svcs via temp credentials.
2. users authenticate via 3rd party IdPs or cognito user pools
   - then leverages iam roles and policies to grant permissions to access aws resources.
3. provide STS credentials for temp access.
3. can assign single iam role for all authenticated users, or role based on user characteristics.
   - like free users or premium users. Premium users can access more resources.
   - guest access.
4. architecture
   1. an app authenticates with 3rd party IdP and receives token. Then Cognito validates token against the IdP and exchange for temp creds.
5. Unauthenticated access - guest access. Not logged in. Best  to have assigned default role.