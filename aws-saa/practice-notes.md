1. **VPC peering** is for private VPCs to talk to each other without traversing the public internet.
2. **aws direct connect** is private dedicated network to connect your onprem to aws.
3. **meta-data/** to append to /latest to access ec2 instance metadata.
4. Resource policy - you attach to the resource being accessed.
5. If you want to minimize maintenance and patching, consider Serverless architecture and svcs.
6. When there is **Principal** in the policy, it is a resource-based policy.
7. ![vpc-peering](./images/labs/vpc-peering.png)
8. ![securecontainer deployment on ecs fargate](./images/labs/secure-container-ecs-fargate.png)
9. almost always, cloudfront is used to front S3.
10. IGW is bidirectional, NAT gw is only outbound.
11. amazon redshift is for data warehousing, not ingestion.
12. site-to-site vpn uses the public internet, so not good for establishing connection between servers with a requirement that conn do not use/traverse public internet.
13. **Amazon S3 Glacier Deep Archive** is the lowest-cost storage class for long-term archival.
14. aws glue is not good for realtime ingesting.
15. S3 is not a file system.
16. you can assign multiple security groups to a resource.
17. aws parameter store does not support auto rotation.
18. Use Amazon Route 53 with a latency-based routing policy and configure health checks for each endpoint.
19. VPC endpts allows VPC resources to privately access aws svcs without traversing public internet.
20. dynamodb DAX is a caching svc for dynamodb.
21. think of AWS IoT core for ingesting data from iot and embedded devices.
22. aws inspector is sast/dast? aws detective is
23. **Gateway Load Balancer** is for easily deploying virtual network appliance. For traffic inspection.
24. **AWS inspection VPC** is a dedicated vpc for routing, monitoring, filtering network traffic between VPCs, onprem, and internet.
25. Use AWS Config rules to configure required settings for aws service and check/detect if the service does not follow this setting. Example, aws svcs should have tags. If there is no tag, detect which svcs and notify.
26. **S3 Intelligent-Tiering** is the ideal storage class for data with unknown, changing, or unpredictable access patterns, independent of object size or retention period. You can use S3 Intelligent-Tiering as the default storage class for virtually any workload, especially data lakes, data analytics, new applications, and user-generated content.
27. Only private subnet EC2s can access RDS.	Need to explicitly allow private subnet instances while blocking everything else