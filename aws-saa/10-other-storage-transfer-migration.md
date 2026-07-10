## aws snow family
1. set of secure appliance that provide petabyte-scale data collection and processing at the edge.
2. for migrating data into and out of aws.
3. services
   1. aws snowcone
      - small, portable, secure device for edge computing.
      - collect, process and move large data to aws efficiently.
      - ship the device to aws (offline), or via datasync (online)
      - good for space and when power are constrained.
      - offerings: snowcone and snowcone ssd
   2. aws snowball edge
      -  jack of all trades device
      -  with onboard storage and compute power
      -  can process data locally, run edge-compute workloads, transfer to or from aws.
      -  data transfer is faster than internet speeds.
      -  3 options: storage optimized, compute optimized, compute optimized with gpu.

## aws storage gateway
1. hybrid cloud strg svc that helps onprem resources with the cloud.
2. 3 types
   1. s3 file gw
   2. tape gw
   3. volume gw
3. s3 file gw
   - setup local s3 file gw to allow nfs/smb connections to s3 buckets.
   - recently accesses data is cached locally
   - easily upload data to s3.
4. amazon fsx file gw
   - low latency perf for frequently accessed data. like s3 file gw.
   - for easy access to amazon fsx for windows file server.
5. volume gw
   - s3-backed storage that you mount locally as iSCI devices.
   - perfect for backup and migration efforts.
   - cached volumes - retain portion of data to cache in local.
   - stored volumes - stored locally
6. tape gw
   - some companies used to and still use physical tapes for backcups.
   - tape gw replace physical tapes with s3-backed cloud storage.
   - cost-effective and durable archive backup.

## aws lake formation
1. fully managed service to govern, secure, globally share data for analytics and ML.
2. allows to create data lake hosted in s3.
3. data lakes are centralized repo for large amount and data. unstructured data.
4. uses aws glue for ETL.
5. for discovering, cleaning and transformation, ingestion
6. aws lake formation workflows/blueprints
   - contain complex multi-job etl activities.
7. access control
8. aws athena, quicksight, EMR, glue
9. use aws lake formation to centralize permission and access to your data lakes.
10. leverage column-level security when using aws quicksight.

## aws transfer family
1. managed service easily move in and out of s3 or efs.
2. supports SFTP, ftp over ssl, ftp, AS2.
3. includes scaling and HA.
4. pay for each endpt per hr and data transfers.
5. can only be used within vpc.
6. use cases: subscription-based data transfer, public data distribution, internal org data transfer, cms, erp.
7. excels at bringing legacy storage to the cloud.

## aws datasync
1. for migrating data between aws and external storage.
2. move data bet nfs and smb, and aws to aws.
3. 2 types of migration
   1. agent based
   2. agentless (aws to aws)
4. destination: s3, efs, fsx
5. concepts
   1. Agents are used to read and write during transfer.
   2. Tasks set source and desti.
6. use cases
   1. move onprem cold data to s3 glacier flexible/deep archive
   2. quickly migrate active datasets over network into aws storage.
   3. copy into any s3.
7. exam scenario
   1. needing to verify data integrity of datasets transferred over direct connect connection.

## aws backup
1. managed service to centralize and automate data protection and backups.
2. think of this when backup is mentioned.
3. configure backup policies. No need for custom scripts.
4. support cross-region and cross-account.
5. works with aws svsc, other clouds, onprem.
6. concepts
   1. Backup Plans - the policy when and how you want to back up
   2. Backup Vault - container that stores backups
   3. supports PITR.

# AWS Backup

## Overview
- Fully managed service to **centralize and automate** data protection and backups
- No need for custom scripts, manual processing, or service-by-service tracking
- Supports **cross-Region** and **cross-account** backups
- Works with AWS services, other clouds, and on-premises virtual machines

---

## Supported AWS Services
Key services with native integration (memorize these):
- EC2 and EBS
- RDS and Aurora
- DynamoDB
- And many more AWS services

---

## Core Concepts

| Concept | Description |
|---|---|
| **Backup Plan** | Policy defining when and how to back up resources |
| **Backup Vault** | Container that stores and organizes backups |
| **Encryption** | All backups are encrypted |
| **Tag-based policies** | Specify backup policies using resource tags |
| **PITR** | Point-in-Time Recovery supported for some resources (e.g. DynamoDB) |
| **Lifecycle management** | Manage backup retention via retention settings |

---

## Backup Schedule Settings

- **Frequency** — every hour, 12 hours, daily, weekly, monthly, or manual
- **Backup window** — time the backup starts + duration in hours
- **Complete within** — maximum time allowed for backup to finish
- **Retention period** — 1 day to 100 years; unspecified = indefinite
- **Transitions** — backups start in **warm storage**, can move to **cold storage** (lower cost) e.g. after 30-45 days

---

## Backup Vault Lock (WORM)
Optional feature

Write-Once-Read-Many — data can be written once and only read after; cannot be overwritten or deleted.

Each vault can have **exactly one vault lock**.

| Mode | Description |
|---|---|
| **Compliance mode** | Strictest — cannot be altered or deleted by **anyone, including root user**. For strict compliance requirements. |
| **Governance mode** | Can be removed by users with specific IAM permissions. Good for **testing** vault lock policies. |

---

## Exam Scenarios to Remember
- **Nightly EBS backups for disaster recovery in another Region** → AWS Backup
- **Long-term DynamoDB/Aurora backups (years)** → AWS Backup (native automated backups limited to ~35 days)
- **Centralized backup management across multiple accounts** → AWS Backup with cross-account support
- **Compliance requirement — backups that cannot be deleted** → Backup Vault Lock in **Compliance mode**

# AWS Migration Services

## The 6 R's of Migration

| R | Name | Description |
|---|---|---|
| 1 | **Rehosting** | Lift and shift — move as-is to AWS. Most expensive, least optimized. |
| 2 | **Replatforming** | Lift, change, and shift — minor modifications before moving to cloud. |
| 3 | **Repurchasing** | Move to a completely different product (e.g. BambooHR → Workday). |
| 4 | **Refactoring / Rearchitecting** | Completely redo architecture using cloud-native features. Most optimized but requires most time and money. |
| 5 | **Retire** | Shut down and get rid of the architecture completely. |
| 6 | **Retain** | Do nothing for now — revisit later after cost analysis. |

---

### AWS Application Discovery Service

Used to **plan** migrations — collects data, does NOT migrate anything.

### What it collects
- Usage data, configuration data, dependencies between applications
- Server hostnames, IP/MAC addresses, disk allocations
- Database engine versions and schemas
- CPU, RAM, disk I/O utilization (average and peak)

### Features
- Group discovered servers into applications
- Track migration status per application
- Integrates with **AWS Migration Hub** for centralized tracking

### Two Discovery Methods

| Method | How | What it collects |
|---|---|---|
| **Agentless** | Deploy OVA file (Agentless Collector) on VMware/vCenter | Hostnames, IPs, MACs, disk, DB versions, utilization data |
| **Agent-based** | Install agent on each VM or physical server (Windows/Linux) | Everything agentless does + detailed processes, network connections, time-series performance data |

> **Exam tip:** Application Discovery Service = **discover and collect data only**, not migrate.

---

## AWS Application Migration Service (MGN)

Automated **lift and shift (Rehosting)** solution — actually performs the migration.

- Replaces the old **Server Migration Service (SMS)** and **CloudEndure Migration**
- If you see SMS or CloudEndure on the exam → think **MGN**

### How it works
1. Replicates source servers into AWS using native cloud services (EC2, etc.)
2. **Stage** resources first — verify everything is ready
3. **Cut over** quickly when ready

### Benefits
- Avoids compatibility issues
- Minimizes performance disruption
- Reduces long cut over windows

### RTO and RPO

| Metric | Value |
|---|---|
| **RTO** (Recovery Time Objective) | Minutes (depends on OS boot time) |
| **RPO** (Recovery Point Objective) | Sub-second — very granular recovery points |

---

## Key Distinction for the Exam

| Service | Purpose |
|---|---|
| **Application Discovery Service** | Discover and collect info about on-prem servers to **plan** migration |
| **Application Migration Service (MGN)** | Actually **perform** the replication and migration to AWS |



## aws database migration service
1. service to easily discover db, convert db schemas, and manage migrating different data stores to the cloud.
2. include rdb, data warehouse, nosql db.
3. to start, you create a DMS server that runs replication software.

exam pro tip: this can migrate db while source db is online.

4. types of migration
   1. homogenous - same db type, like sql server onprem to sql server in rds.
   2. heterogenous - different db, like oracle to aurora.
5. Replication tasks move set of data from source to target endpt.
6. there are 3 migrations
   1. full load - migrates data from source db to target db. Best if you can afford downtime.
   2. full load + change data capture (CDC) - performs full load while capturing changes on the source. Changes applied to target after.
   3. CDC only - meant to replicate data changes. To keep source and target in sync.
7. aws dms source endpts
   1. on prem or ec2 db (oracle, ms sql server, postgres, mariadb, mysql, etc)
   2. 3rd part managed db like azure and gcp.
   3. aws rds db
   4. aws s3
   5. aws documentdb
8. aws dms target endpts - just like source endpts and more.
   1. aws redshift and redshift serverless.
   2. dynamodb and s3
   3. opensearch service and aws elasticache.
   4. kinesis data streams and kafka
   5. documentdb and aws neptune

## database schema conversions
1. 2 options for db schema conversion
2. dms schema conversion
   - web service
   - assess complexity of migration.
   - convert db schemas and objects before applying to target.
   - converts source db schema and most db objects to format compatible with target db.
   - will include tables, views, stored procedures, functions, etc.
   - if cant convert the object, it will be clearly marked for manual conversion later on.
   - supports less db platform, less func, less supp sources compared to SCT.
3. aws schema conversion tool (SCT)
   - downloadable/installable tool
   - convert existing db scheam from one db engine to another.
   - works with OLTP schema, data warehouse schema (OLAP), even nosql.
   - for HETEROGENOUS db engine migrations.
   - example: sql server to aurora mysql, snowflake to aws redshift, cassandra to dynamodb
