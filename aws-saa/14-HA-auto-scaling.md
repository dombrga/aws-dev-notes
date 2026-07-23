## Scalability
1. ability to increase of decrease performance due to demand.
2. vertical vs horizontal scaling.

## auto scaling groups (ASG)
1. asg contains collection of ec2 instances.
2. offer self-healing and cost opti
3. scale out - add ec2
4. scale in - remove unneeded ec2
5. Launch Template
  1. specifies settings for building ec2 instances.
  2. AMI and instance type, ebs vol, ssh key pairs, iam role, vpc networking info, elb info.
6. Launch Configuration is deprecated, use Launch Template.