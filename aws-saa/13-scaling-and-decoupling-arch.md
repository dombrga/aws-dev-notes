## regions, AZ
1. AWS regions - highest level of abstraction
  - ~39 regions atm, more coming soon.
  - GovCloud region.
  - for redundancy and connectivity.
  - Consists of at least 3 AZs per region.
2. Edge location
  - amazon works with telecom carriers around the world.
  - helps in latency and bandwidth.
  - connected to Regions.
3. AZ is its own distinct, geographically separated data center
4. AZ IDs are critical to know.
5. high availability (HA) and fault tolerance (FT).
  - HA is about ability to self-recover after component failure.
  - ability to switch service/apps from failed components.

## elastic load balancing (ELB)
1. auto distributes incoming app traffic across multiple targets on the backend. Handle load and distributes.
2. typically across multiple AZs.
3. can setup DNS to point to ELB.
4. ELBs monitor health of backend targets. Will only route to healthy ones.
5. can implement ssl/tls termination.

Pro tip: create tiers to separate public and private network traffic.

6. 4 types
  1. ALB
  2. NLB
  3. GWLB
  4. CLB - first version and avoid this.
7. ELB schemes
  1. internet-facing (public) - deployed into public subnets; route reqs over the internet using public IP.
  2. internal (private) - deployed into private subnets.
8. routing alg
  1. round robin - sequential order.
  2.  least outstanding req - route to target with lowest # of in progress requests
  3.  weighted random - route reqs evenly across healthy targets. Can use automatic target weights.
9. Health checks - can set ELB to periodically send reqs to test status. Healthy targets are considered InService.

**Remember**: multi-tiered VPC arch designs are best practice.

**exam scenario:** app on ec2 instances in multi AZ. Internet facing ELB for customer to use. Only allow access to EC2 instanes from ALB. Deploy ec2 in private subnet.

## application load balancer (ALB)
1. works in layer 7.
2. supports content-type, cookies, custom headers, other layer 7 attribs.
3. can listen only to http or https.
4. supports websockets, http/2.
5. perfect for containerized apps.
6. ALB components
  1. Listener - can define rules to determine how reqs are routed to targets.
  2. Rules - attached to Listener.
  3. Target Group - composed of targets. EC2, lambda funcs.
7. target types
  1. target types: ec2 instances, ec2 tasks, lambda func, private IPs.
8. must deploy at least ssl/tls cert to use https listener.
9. Alias record for custom dns.
10. X-forwarded-for, x-forwarded- port, x-forwarded-proto
11. Port Mapping: ecs feature
12. ALB IP change, so dont use it. Use its dns name.