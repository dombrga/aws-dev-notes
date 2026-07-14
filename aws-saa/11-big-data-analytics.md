## amazon redshift
1. 3 V's of big data - defining properties or dimensions of big data and processes
   1. volume- amount of data
   2. velocity - speed of processing, collection, analysis
   3. variety - # of types of data stored and used.
2. redshift is fully managed pb scale data warehouse.
   - based on postgres but for big data and OLAP workloads instead.
   - use standard sql and BI tools to interact with it.
   - up to 10x perf
   - columnar storage
   - parallel query engine
3. 2 cluster deployment modes
   1. provisioned - collection of compute nodes and leader node. You manage.
   2. serverless - auto provision and management. Set baseline capacity.

### amazon redshift HA, snapshot, DR
1. supports multi-AZ deployments, spans 2 AZs.
2. single-az is default for provisioned clusters.
3. snapshots for incremental and PITR.
   - snapshots can be automated or manual stored in s3.
   - snapshots can be copied across Regions automatically.
   - include infor about cluster, like # of nodes, node type, etc.
4. you typically want to load data into redshift using large inserts for perf.
5. redshift data ingestion example
   1. tb of data from clickstream, mobile, web app ---> kinesis data stream ---> kinesis data firehose ---> redshift
6. Enhanced VPC routing - forces COPY and UNLOAD operations through a VPC. Allows of security access controls, sec grps, NACLs

### amazon redshift spectrum
1. service to efficiently read from amazon s3 using redshift without having to load data first.
2. required existing redshift cluster.
3. queries use a lot less processing capacity.

## amazon elastic mapreduce (EMR)
1. ETL
   1. Extract - data is retrieved from a source
   2. Transform - data is cleaned, formatted, prepared for storage in target system
   3. Load - transformed data is loaded into the target system.
   4. use cases: customer analytics. financial risk assessment, recomm engines.
2. EMR is service to help with ETL processing.
3. mangaed big data platform for hadoop clusters.

exam pro tip: mention of large and hadoop, think EMR.

4. Hadoop distributed file system (HDFS) - file system for hadoop that distributes stored data across intances.
5. EMR file system (EMRFS) - extends hadoop to ad ability to directly access data stored in s3
6. local file system - locally connected disk created with each ec2 instance.
7. clusters are groups of ec2 instance within EMR. Each instance is a node.
8. 3 types of node:
   1. primary - manages the cluster
   2. core - runs tasks, stores data in hdfs, long-running
   3. task - optional nodes that only run tasks.
9. purchase option
   1. on-demand
   2. reserved
   3. spot
10. EMr use cases: ETL, web indexing, genomics

## aws glue
1. serverless data integ service.
2. to easily discover, prepare, combine or transform data.
3. perform ETL serverless.
4. connect to 70+ sources and manage data.
5. concepts
   1. data catalog - metadata store; table definition, job feniitions and other control info for ETL workflows.
   2. crawlers - connect to your data sources, infer data scheams, and create metadata table definition
   3. etl jobs - extract data from sources, trasform data using apache spark scripts, and load data into targets.
   4. triggers - resources or methods to start jobs.