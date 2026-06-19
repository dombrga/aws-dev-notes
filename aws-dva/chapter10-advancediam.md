10.1 web identity federation
- simplifies authen and autho for web apps
- gives access to aws resou after succ auth with a web-based identity provider like fb, google
- will receive authe code
Amazon cognito.
1. Provides web id fed for sign in and up, and access guest user
2. identify broker - manages authe bet your app and web id provider
3. sync multiple devices
4. recom approach for mobile
5. provides temp credential. This maps to IAM role
6. secure and seamless
- user pools. User directories used to manage sign ups and in func for mobile and web app
- sign-in. Sign-in to user pool or using fb, amazon, or google
- identity pools. enable to provide temp credentials. Allows user to access aws resources
- user pools give user jwt token. This will be exchanged to an aws credential using identity pool
- cognito push syncronization. Push updates and syncs user data across multiple devices. SNS silent notif

10.5 inline vs managed vs customer managed policies
- iam is used to define user access permission
1. managed policies - created and administered by aws. 
- likeAmazondynamodbfullaccess, awscodecommitpoweruser, amazonec2readonlyaccess. 
- Assign permissions without having to write policy yourself. 
- Can be attached to multiple users, groups or roles
- Cannot change permissions
2. customer managed policies
- created by you
- you can copy existing aws managed policy and customize it
- for your own specific needs
3. inline policy
- strict 1:1 relationship between entity and policy
- user, group, or role
- cannot attach inliny policy to multiple entities
- when you delete the entity the inline policy is attached, policy is also deleted

- recommended is managed policy

10.7 STS assumedrolewithwebidentity
sts api
- assume-role-with-webo-identify is an api provided by sts, security token service
- returns temp security creds
- cognito uses sts assume role 
- for regular web apps, you can use sts
- assumedroleuser. arn and asummedroleid to programatically reference the temp creds

10.8 configuring cross account access
cross account access
- delegate access to resources to different aws accounts that you own
- by using iam role
- able to switch roles, no pass required