### dynamodb
1. nosql db service of aws.
2. good for unstructred data.
3. automatically handles scaling for massive workloads.
4. high performance single digit ms, supports millions of request/sec.
5. mobile apps, web apps, online gaming
6. hundreds of tb storage.
7. consists of tables, rows (items) and columns (attributes)
   1. each item can be up to 400 kb size. unlimited items.
   1. attributes can change over time. Can add or remove anytime.
   2. have unique primary key (partition key). Single or composite pk.

### dynamodb HA and monitoring
1. dynamodb auto replicates data across 3 AZ.
2. 99.99% SLA.
3. zero downtime maintenance, handled by aws.
4. monitoring
   1. cloudwatch - monitors tables and reports metrics
   2. cloudtrail - capture api calls and related events. Logs and and can be analyzed.
5. dynamodb tables are regional resources.

### dynamodb capacity modes
1. provisioned mode
   1. manually define amount of capacity required
   2. write capacity unit (WCU)
   3. read capacity unit (RCU)
   4. pay for provisioned capacity units even if not in use.
   5. requires planning.
2. on-demand mode
   1. flexible capacity mode
   2. read/write auto scales on demand.
   3. pay per req.
   4. for unpredictable or spiky workloads.
3. strongly consistent - data immediately returned
4. eventually consistent
5. scan, query
   1. Scan - reads every item in table and returns all data attribs. More resource intensive.
   2. Query - find items based on PK.
6. dynamo db auto scaling
   - dynamically adjust provisioned throughput capacity.
   - you create scaling policy

### dynamodb security
1. dynamodb is publicly accessible service by public endpt.
2. you need to leverage iam to control access and auth to tables.
3. encryption at rest by default.
4. leverage vpc endpts to keep traffic within aws. Also use resource-based policies.

### dynamodb global table
1. deploys multiregion, multi master db. Identical tables in diff regions.
2. provides low latency
3. for active-active implem. Means can read/write to any table within region.
4. dynamodb streams must be enabled.

### dynamodb streams
1. time ordered sequence of item level operations.
2. create, update, delete.
3. stored up to 24 hrs.
4. commonly combined with lambda funcs for triggering workloads.
5. Stream specs
   1. StreamViewType - what kind of info to be written in the stream.
      1. KEYS_ONLY - key attribs of modified item
      2. NEW_IMAGE - item after the operation
      3. OLD_IMAGE - item before
      4. NEW_AND_OLD_IMAGES - new and old

### dynamodb accelerator (DAX)
1. managed, HA, in-memory cache for dynamodb.
2. up to 10x perf improvement. ms to microsec.
3. compatible with dynamodb api calls.
4. writes are write-through. That is, write to Dynamodb first, then to DAX cluster.
5. Eventually consistent reads
   - default behavior
   - attempt to read in DAX. If not there, read in dynamodb.
6. strongly consistent read
   - dax forwards reads to dynamodb. Results not cached.

### dynamodb item TTL
1. delete item at some specified expiration time.
2. cost saving method.
3. not immediately deleted, but within few days of TTL.

### backups
1. aws Backup or via dynamodb itself.
2. aws Backup can implement auto backup.
3. via dynamodb
   - on demand backup
   - point in time recovery (PITR) - continuous backups managed by dynamodb; 35 days of recovery points.
   - no impact on performance and availability.
   - encrypted already.
   - charged on size and duration.
4. importing data
   - csv, dynamodb json, ion
   - no impact on write capacity
   - creates new table, not existing table.
   - gets logged to cloudtrail
5. exporting data
   - requires PITR turned on.
   - no impact on read capacity.
   - for auditing, ETL, data analytics.
   - full or incremental dynamodb json or ion format.