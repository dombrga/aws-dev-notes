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
  3. tagging and versioning - put tags in image or prevent tags from being modified.
8. Commonly integrated AWS services
  1. amazon ecs
  2. amazon eks

## amazon ecs
1. service to easily launch and manage docker containers.
  1. easily manage anywhere from 1 to 1k conts.
  2. appropriate kepps them online. Self-healing.
  3. can easily registered with ELBs.
  4. containers can have individual roles (Task role).
2. ECS cluster - logical grouping of tasks (conts). Controlled by the launch type you choose.
3. Launch types
   1. ec2
      - you choose instance types, # of instances you want to run within ecs clusters. Run multi containers on once intance.
      - must run the ECS agent.
      - aws handles starting and stopping of containers, but you maintain ec2 instances, like patching.
      - large, long running workload
  1. fargate
      - serverless, pay-as-you-go offering.
      - You do not provision and manage infra.
      - you create a Task Definition.
      - you specify CPU and ram reqs/limits
      - large workloads and reduce operational overhead; small, burstable workload with no resource intensive reqs; periodic, batched workloads.
  1. ec2 anywhere
4. cost saving
   1. spot instances for ecs ec2
   2. compute saving plan.