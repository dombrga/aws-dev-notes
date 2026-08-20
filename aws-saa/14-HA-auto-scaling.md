## Scalability
1. ability to increase or decrease performance due to demand.
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

## asg policies
1. ways to scale
   1. manual
   2. simple - relies on differnet metrics like cpu utilization. Straightforward scaling
   3. target tracking - scaling metric/value that should be maintained at all times
   4. step scaling - for example, add 5 instances if >=60% cpu util, 10 more if >=80%.
   5. predictive - forecast future needs
   6. scheduled scaling
2. ASGAverageCPIUtilization
   - avg CPU utili is maintained at a set threshold.
   - scale out at >= 60%
   - scale in <60%
3. ASG cooldown period - wait before completing any scaling activities.

## asg health check
1. ec2 - check ec2 instance status and underlying hardware.
2. elb - asg can be part of a target group of elb.
3. vpc lattice - not common
4. ebs
5. custom health checks - pretty rare.
6. Grace period - delay health check, default 300 secs.

## asg instance maintenance policies
1. launch before terminate - availability is important.
2. terminate before launch - cost is important

## ASG lifecycle hooks
1. perform actions on instances during lifecycle events.
2. up to 2 hrs of waiting.

**Exam Scenario:** instances created by ASG need to check in to third party auditing tool when they launch or terminate. Can use lifecycle hooks to run this.

## vpc lattice
1. managed app networking service to connect, secure, monitor services for your app in vpc.
2. similar to kubernetes, like service mesh.