## June 25, 2026

### RDBMS
1. db system in the form of tables.
2. tables, rows and columns.
3. types of processing
   1. OLTP
      - primary purpose is to process db transactions.
      - like processing orders, updating inventory, managing customer accts.
   2. OLAP
      - to analyze aggregated data, generate reports, perform analytics.
4. most RDBMS use SQL.

### AWS RDS
1. database service of aws.
2. setting up and managing rdbms.
3. sql server, oracle, mysql, postgres, mariadb, etc.
4. rds handles
   1. backups
   2. patching
   3. auto failure detection and recovery
5. highly available
6. access controls
   1. IAM
   2. VPC sec grp
   3. NACLs
   4. encryption at rest and in transit
7. you provision a DB instance, like an ec2 instance. Can host 1 or more db.
8. DB instance classes - compute and memory capacity
   1. general purpose: db.m*
   2. memory optimized
   3. compute optimized
   4. burstable performance.
9. instance storage types
   1.  provisioned iops ssd - i/o intensive workloads
   2.  general purpose ssd - best for dev and testing
   3.  magnetic - not recommended
   4.  sample: db.m5.large

### rds networking
1. db instances are created within a vpc.
2. best practice to isolate db instance within their own subnet.
3. db subnet group - vpc subnets specific to db instances.
4. network access is controlled via VPC sec grps.
5. db instance can have public ip. Not recommended.
6. db instance not accessible via ssh.