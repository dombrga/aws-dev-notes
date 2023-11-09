chapter 3
- cannot encrypt AMI after it is created. Need to recreate and encrypt
- for ec2 instance to access aws resource, it should have permissions attached to it

- application load balancer for http and https
- network load balancer for tcp and high performance 
- classic load balancer for http/https/tcp


3.10 route53
- aws DNS service. 
- to map domain name you own

3.15 rds
- sql server, oracle, mysql, postgres, aurora, etc. aws aurora is aws' own sql db, compatible with mysql and postgres.
- multi-az, failover capab, automated backup

3.16 rds demo
- edit security group of rds for ec2 to connect to rds

3.1 multi-az and read replica
- multi-az (standby instance) is copy of primary db for disaster recovery in another AZ. When primary db fails, failover process will execute and multi-az will be used
- read replica is a copy of primary db used for read operation for scaling performance. Required automated backup. Can be promoted to become a primary db

3.19 rds proxy
- rds proxy is serverless
- preserves app connection during failover
- deployable to multi-az

3.20 elasticache
- in-mem cache 
- improves db performance. Can store frequently accessed data
- for storing session data 
2 kinds
1. memcached - basic obj sharing 
   - scales horizontally, no persistence, multi-az or failover 
   - simple caching
2. redis - persistence, multi-az, failover

3.21 memorydb for redis
- redis-compatible
- massively scalable in-mem db (gb to >100 tb)
- high available. Multi-az. transaction log for recovery and durability
- can be a primary db, data can be stored in memory (instead of db+cache)
- ultra fast performance
