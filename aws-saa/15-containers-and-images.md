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