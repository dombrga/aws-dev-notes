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

