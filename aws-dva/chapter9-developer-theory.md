9.1 intro to ci/cd
- software dev practice. continuous integration, delivery/deployent
- make small code changes, then automate activities after, like code integration, build, test, and deployment
- enables rapid deployment

For Continuous integration
CodeCommit - source and version control service. Code repo

For Continuous delivery
CodeBuild - automated build. Compiles source code, runs tests and produces packages that are ready to deploy

For Code deployment
CodeDeploy - automates code deployments to any instance like ec2, lambda, onprem

CodePipeline - end2end solution, build test, and deploy

9.2 CodeCommit 
- enables collaboration, like github, gitlab.

9.5 CodeDeploy
- automated deployment
- works with ec2, onprem, Lambda
- quickly release new features, avoid downtime during deps
2 approaches
1. in-place - aka rolling update.
app is stopped on each instance and new release is installed. Capacity is reduced during dep. Lambda not supported. New version is called revision. When something went wrong, you need to redeploy previous version
2. blue/green - new instances are provisioned and new rele is installed on new instances. Blue is active dep, green is new rele. Easy to switch between old and new. SAFEST OPTION!

9.6 CodeDeploy appspec file
- a config file. Defines params to be used during codedeploy dep
- ec2 and onprem systems, yaml only
- lambda. yaml and json suported
Parts of appspec file
1. version. reserved for future use. 0.0 only allowed value
2. os
3. files. config files, packages
4. hooks. lifecycle event hooks. scripts that need to run at specific points in dep process
- appspec.yml must be in the root dir of revision or dep will fail

9.7 CodeDeploy lifecycle event hooks
- Run Order
in place deployment hooks. 3 phases - de-registering from load bal, installation, reregister to load bal
- BeforeBlockTraffic, BlockTraffic, AfterBlockTraffic, 
- ApplicationStop, DownloadBundle, BeforeInstall, Install, AfterInstall, ApplicationStart, ValidateService. For installing app
- BeforeAllowTraffic, AllowTraffic, AfterAllowTraffic

9.9 CodePipeline
- fully-managed ci/cd service
- orchestrates build, test and dep
- pipeline is triggered everytime there is a change in code
- automated release process
- integrates with codecommit, codebuild, codedeploy, github, jenkins, elas bea, cloudformation, Lambda, ecs

9.14 CodeArtifact
- an artifact repository for finding software packages thats needed\
- store, publish, and share artifacts like packages, a bundle of software. Includes oss and in-house. 
- central repo
- integrates with npm, pypi, maven central
- integrates with ci/cd system, like CodeBuild
- examples of artifacts docs, compiled apps, deployable packages, libraries
- integration with pub repo is important. Approved packages. Efficient
Integrating with public repo
- create a domain, which is a grouping of repo
- create a repo in the domain. This is where packages is stored
- create upstream repo that will connect to the external pub repo. This will allow to pull packages from the external repo. Everything is encrypted
- connect repo to the upstream repo

9.16 aws ecs
- run containerized workloads
- containers are similar to vm. A virtual operating env. Standardized unit with everything the software needs, like libs, system tools, code, and runtime
- dockers or windows containers
- ecs is orchestration service. Quickly deploy and scale containerized workloads without installing, configuring, and scale you own orches platform
- deep integ to iam, vpc, and route53
- choice of clusters of vm or fargate for serverless. EC2 will give more control
- Elastic container registry. If you have docker images already create ECR. ecr is just a registry/place to store container images. ECS connects to the registry and uses the image to deploy docker conts
- sagemaker for ml modesl for training and inference. aws lex for deep learning. amazon.com recom engine uses ecs

9.17 CloudFormation
- manage, configure, and provision your AWS iaas. 
- using cloudformation template in yaml or json.
- consistent, fewer mistakes. Quick and efficient. Version control and peer review. Free to use. manage updates and deps. easy rollback
Process of using CLoudFormation
1. write the template in yaml/json
2. upload to cloudformation using s3
3. cloudformation reads the template and makes the API calls
4. a resulting stack is created
Some fields of cloudformation template
1. awstemplateformatversion
2. parameters - input values
3. conditions - to test condition and take action depending on cond. Mappings is for setting values based on region
4. Transform - include code snippets outside of template. For referencing additional code. Lambda
5. Resources - ONLY mandatory field and most important. Lists aws resources to deploy
- AMI and amiId is region specific

9.20 cloudformation
- you can use Outputs section of template to export values from one stack to another using ImportValue function

9.21 server application model SAM
- extension of cloudfor for serverless apps
- simplfied syntax. APIs, Lambda, dynamo
sam commands
1. sam package - takes template file and uploads to s3 
2. sam deploy - takes sam template, name of stack, and capabilities for iam
- sam cli

9.23 nested stacks
- stacks that create another stack. Enable reuse
- example is standard config for a load bal, web server, or app serer
- Type: AWS::CloudFormation::Stack. 
- TemplateURL - file located in s3

9.25 cloud dev kit
- to build apps, define and deploy aws resources using prog lang. ts python, java, .net, go
app - container of 1 or more stack
stack - unit of dep
construct - defines aws res
1. model your app using pl
2. use cdk to transform to cloudfo template
after you code
1. create new cdk project cdk init
2. compile the app. npm run build
3. cdk synth
4. cdk deploy

9.27 aws amplify
- set of tools and services to develop web and mobile apps easy
- stable and reliable backend. client libs and cli
- fe devs can focus on development. Amplify takes care of auth, storage, Lambda funcs and more. Integrated with services like cognito, s3, Lambda and api gateway
1. amplify hosting - fully managed web hosting service. Web app and static website hosting. with ci/cd. integrates with code repos
2. amplify studio - simple visual ui, separate from aws man console. creates frontend ui. configure nad maintain app backend. features like auth, data services, and serverless funcs
- you can upload code to repositories like gitlab and amplify hosting will deploy when there is a change detected