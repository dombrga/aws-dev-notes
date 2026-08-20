## Containers, images
1. Dockerfile - document that contains commands or instructions to build an image.
2. image - immutable file that contains the code, libs, deps, and config files needed to run an app.
3. Registry - stores docker images for distribution. Private or public.
4. container - a running copy of the image.
5. use cases. Microservices; lift and shift

## amazon ecr
1. service to store and manage docker images.
2. supports public and priv repo.
3. supports OCI images and artifacts.
4. private repo is controlled by aws iam permissions.
5. lifecycle policies to manage images, like expire old images.
6. cross region and cross acct repli.
7. Concepts
   1. image scanning - identify software vulnerability as they are pushed.
   2. encryption - protect container images at rest with aws kms keys.
   3.  tagging and versioning - put tags in image or prevent tags from being modified.
8.  Commonly integrated AWS services
    1.  amazon ecs
    2.  amazon eks

## amazon ecs
1. service to easily launch and manage docker containers.
  1. easily manage anywhere from 1 to 1k conts.
  2. appropriately keeps them online. Self-healing.
  3. can easily registered with ELBs.
  4. containers can have individual roles (Task role).
2. ECS cluster - logical grouping of tasks (conts). Controlled by the launch type you choose.
3. Launch types
   1. ec2
      - you choose instance types, # of instances you want to run within ecs clusters. Run multi containers on once intance.
      - must run the ECS agent.
      - aws handles starting and stopping of containers, but you maintain ec2 instances, like patching.
      - large, long running workload
   2. fargate
      - serverless, pay-as-you-go offering.
      - You do not provision and manage infra.
      - you create a Task Definition.
      - you specify CPU and ram reqs/limits
      - large workloads and reduce operational overhead; small, burstable workload with no resource intensive reqs; periodic, batched workloads.
   3. ec2 anywhere
4. cost saving
   1. spot instances for ecs ec2
   2. compute saving plan.

## amazon ecs concepts
1. Task definition
   - json formatted doc that is the blueprint of the containerized app.
   - role, launch type, cpu/memory, network config, env vars.
2. Task role
   - can optionally have iam role to allow aws api calls. Like s3:GetObject, kms:Decrypt, sqs:ReceiveMessage.
   - Gets assigned to the task (container)
3. Task Execution role
   - aws iam role that allows containers on outside to make api calls.
   - Service itself uses this role.
   - used for pulling image from ecr, getting data in secrets manager.

## load balancing ecs
1. Service - allows you to maintain a specified # of instances of a task defn. Allows for HA.
2. ecs services can be integrated with ELB to distribute traffic across the tasks that belong to the svc.
3. ALB, NLB, CLB. Avoid CLB.
4. Application Auto Scaling
   - for auto scaling resources other than ec2.
5. ecs published CW metrics with the svc's cpu and memory usage.
   - ecs service auto scaling and app auto scaling leverage these metrics.

## ecs storage
1. amazon ebs: db, root volums, etl workloads.
2. amazon efs: data analytics, media proc, cms apps.
3. FSx for windows file server: .net apps for windows file storage.
4. docker volumes - sharing volumes on different containers on same host.
5. bind mount - mounting host volume for data persistence.
6. fargate and aws efs offer fully serverless solution.

## amazon eks
1.
   1. cluster; node - vm or physical machine hosting running apps with in containers, like ec2
   2. pods
   3. service - feature for exposing app
   4. jobs - one-off tasks that run until completed and then stop.
   5. ingress - object in k8s that sets up external access to the services in the cluster. Via http and load balancing
   6. storage - Persistent Volumes (PV) are objects for strg in a cluster and independent of pods
2. aws-managed svc for any k8s workload.
3. similar to ecs, but for k8s.
4. Node types
   1. managed node grps - allows aws to manage and provision nodes for use of eks clusters.
   2. self managed nodes - nodes you deploy with an AMI.
   3. aws fargate - serverless offering. Everything is managed for you, just need to specify what Pods to deploy.
5. Eks cost opti
   1. Spot instances support managed and self managed node grps.
6. Scaling eks
   1. Kubernetes Metric Server
   2. horizontal pod autoscaler
   3. cluster autoscaler
7. K8s is cloud-agnostic solution for cont orchest.

## eks data storage
1. how to store data locally in your cluster?
   1.  ebs
   2.  efs
   3.  FSx for lustre, netapp ontap, openzfs
   4.  s3
2. concepts
   1. StorageClass - to configure default settings for ebs vol
   2. amazon ebs container storage interface (CSI)

**Exam pro tip:** HA, scalable, shared file system for eks pods? EFS is great.

## securing eks
1. EKS roles
2. Service Account - gives pods ability to assume identity. In aws, by IAM role.
3. EKS Pod identity - to assign iam role to svc acct so they can make aws api calls.

## amazon eks distro (eks-d)
1. k8s distro based on and used by eks.
2. has same versions and deps deployed by eks.
3. fully managed by you, unlike eks.
4. you can run eks-d anywhere, like onprem, in cloud, or somewhere else.

## amazon eks anywhere
1. on-prem eks - onprem way to manage k8s clusters with same practices as eks.
2. like eks-d
3. k8s control pane management is operated completely by customer.
4. amazon ECS Anywhere
   1. for managing container-based apps onprem
   2. no need to install and operate local container orches software.
   3. enables standardization of container mgmt across envs.
   4. no ELB support means lb could be less efficient.
5. amazon eks connector
   - register and connect k8s to be viewable in eks
   - want to view all clusters from k8s and onprem in one location.

## aws app runner
1. svc for deploying from source code or container image to a secure web app.
2. allows to focus on code and images by directly connecting to repositories.
3. use case
   1. simply deploying updated versions of code or cont images.
   2. auto deployments when commit is pushed.

**Exam pro tip:** AWS app runner is good option for inexperienced teams, no devops team, that need to quickly deploy app.

## aws App2Container
1. CLI to lift and shift apps into containers
   - ecs
   - eks
   - app runner
2. Java, asp.net