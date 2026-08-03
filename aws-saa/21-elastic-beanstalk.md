## PaaS
1. PAAS is a complete development and deployment env hosted in cloud.
2. hosting provider handles infra like db mgmt, middleware, ci/cd.
3. you only manage and worry about the app.
4. easier automation, faster deployment, simple integration

## elasic beanstalk
1. managed service meant to be one stop shop for everything PaaS.
2. let devs worry about development and not infra.
3. create template and will automate your deployment.
4. easily upload code, test and deploy to multiple env.
5. supports java, .net, python, ruby, php, node, go, docker, tomcat.
6. Deploy multitiered, HA, architecture
   1. ec2
   2. ALBs
   3. ASG
   4. even RDS if you want. But not best practice.
7. **Exam scenario:** need a HA, managed solution with minimal overhead when migrating java (or others) app to aws.

## EB env and application
1. Application - logical collection of beanstalk components
   1. environments
   2. version
   3. configurations (similar to folder)
2. Application version - specific iteration of code of app. Points to an s3 obj containing code.
3. Environment - collection of aws resources running app version.
   - you run a single app version at a time, per env.
4. Environment Tier - to let you know the type of app being ran and underlying resources.
   1. Web server - deploys maanged ASG behind ELB with CNAME url
   2. worker tier - deploys ASG that scales based on msgs in SQS queue.