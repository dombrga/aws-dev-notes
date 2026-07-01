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

## June 26, 2026

### rds backups
1. automated backup
   - specify a backup window.
   - rds creates a volume snapshot of db instance. First snapshot is entire db instance, after are incremental.
   - set retention period (0-35 days). 0 if you want to disable retention.
   - backups are stored in s3, but no access to the storage.
   - can be replicated cross-Region.
2. manual backup
   - manual backup trigger
   - retention is manual
   - you create new db instance by restoring a snapshot.
   - you cannot restore to an existing db instance.
3. you pay for rds storage even if you have stopped rds instance.

### multi-az and HA
1. In multi-az
   - creates exact copy of db in another AZ called standby replica. You cannot directly read/write from the standby.
   - aws automatically handles data replication between primary and standby
   - protection from instance failure and downtime.
   - multi-az deployment model
     1. instance deployment - has one standby db instance by default.
     2. cluster deployment - 2 standby instance
   - not meant for scaling, only for failure and disaster recovery and resiliency.
2. db instance failovers for multi-az takes 60-120 secs.

June 29, 2026

### read-only replica
1. read-only copy of instance to reduce load to primary db.
2. great for read-heavy workloads. Purpose is for scaling.
3. read-only replica has its own dns endpoint.
4. same az, cross az or cross region.
5. need to have auto backups enabled.
6. can be promoted to be its own database.
7. 2 deployments
   1. instance read replica
   2. cluster read replica

### rds auth
1. options
   1. password auth
   2. aws iam auth - auth token based on iam credentials
   3. kerberos auth - external auth of db users via kerberos or AD
2. RDS integrates with aws secrets manager
   1. creds are encrypted via aws kms.
   2. not free
   3. auto rotate

### rds encryption
1. in transit and at rest
2. rds has tls by default for encryption in transit.
3. also has encryption at rest. Logs, backups, snapshots are encrypted. Must be enabled at creation. Cant change kms key once created, need to create new.
4. for oracle or sql server, use transparent data encryption (TDE)

### cost optimization
1. data transferred during cross region replication incurs charges.
2. you pay for: rds instance, data transfer, db storage, monitoring (optnal)
3. pricing opts
   1. on demand - by the hour you use
   2. reserved - 1 yr or 3 yr term with discnt
   3. Leverage RI. no rds spot instance.

### RDS custom
1. only for oracle and ms sql server. You connect via ssh or session manager
2. allow for os and db customization.
3. config more detailed setting, install own custom patches, non rds native db features.

### rds proxy
1. fully managed, HA db proxy. You enable after you create db.
2. makes app more scalable and resilient to failures.
3. allows aps to pool and share db conn.
4. reduce memory and cpu overhead of opening conn.
5. handles unpredictable surges in db traffic.
6. must be accessed via vpc. No public access.
7. serverless and autoscaling.
8. usually does not require code changes.
9. can create read-only endpt for aws aurora.
10. optimize conn from aws lambda funcs.