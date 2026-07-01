### amazon aurora
1. fully managed rdbms compatible with mysql and postgres.
2. managed via aws rds, an engine type.
3. difference between trad rds?
   1. proprietary
   2. cloud optimized performance, more performant.
   3. cost roughly 20% more.
4. compute
   1. can scale up to 96 vcpus
   2. up to 768 gb of memory.
5. you deploy aurora in aurora db cluster.
6. db cluster consists one or more db instance and a cluster volume. Cluster volume - storage volume that spans multi az
7. 2 types of cluster
   1. primary
   2. replica
8. aurora db cluster endpts
   1. cluster endpt - primary db instance
   2. reader endpt - aurora replica
   3. custom endpt

### aurora storage
1. high perf storage system that auto scales
2. minimum 10gb, max 128tb
3. data redundancy
   - 2 copies of data in each AZ spread across 3 AZ.
   - total of 6 copies.
   - auto recovers in a healthy AZ.
4. self healing

### aurora replica
1. primary instances support read and write.
2. theres only 1 primary (writer) instance in a cluster.
3. aurora replica only support read replica.
   1. will be a failover target automatically.
4. support cross region replication.

### aurora HA and scaling
1. auto scaling dynamically adjusts # of replicas.
2. primary instances are auto repli across AZ to replicas
3. promote replica to become primary. Faster than recreating.
4. promotion depends on priority. 0-15, 0 highest priority.

### aurora backup
	1. auto backup
	2. 1 or 35 days retention
	3. stored in s3
	4. you can take manual snapshot.
	5. you cam backtrack. Only in mysql compatible. Not replacement or db cluster backup.
	6. limit for backtrack window is 72 hrs.
	7. aurora cloning allows faster db cloning. To setup test envs. Experiment with potential changes. Run intensive ops and testing.

### aurora serverless
1. on demand auto scaling option. Infrequent, unpredictable workloads.
2. can be more cost effective.
3. good for development and initial testing.
4. ACU
   - aurora serverless capacity units, unit of measure.
   - each ACU provides 2 gibibytes of memory.

### aurora global db
1. DR solution that spans multiple aws regions.
2. low latency global reads and DR regional outages.
3. 1 primary aws region where data is written and managed, up to 5 read only secondary aws regions.
4. replication between regions is <1 sec. up to 16 read replicas/region. DR and promotion of region is <1min
5. globaldb operations
   1. global db switchover - for planned operational procedures like regional rotations
   2. global db failover - for recovery

### aurora ML
1. incorporate predictions via different ML services in aws.
2. aws bedrock, aws comprehend, sagemaker.
3. detect fraud within apps, customize marketing, recommend products.