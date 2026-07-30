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