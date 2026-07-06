### aws snow family
1. set of secure appliance that provide petabyte-scale data collection and processin at the edge.
2. for migrating data into and out of aws.
3. services
   1. aws snowcone
      - small, portable, secure device for edge comp.
      - collect, process and move large data to aws efficiently.
      - ship the device to aws (offline), or via datasync (online)
      - good for space and power are constrained.
      - offerings: snowcone and snowcone ssd
   2. aws snowball edge
      -  jack of all trades device
      -  with onboard storage and compute power
      -  can process data locall, run edge-compute workloads, transfer to or from aws.
      -  data transfer is faster than internet speeds.
      -  3 options: storage optimized, compute optimized, compute optimized with gpu.

### aws storage gateway
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

### aws lake formation
1. fully managed service to govern, secure, globally share data for analytics and ML.
2. allows to create data lake hosted in s3.
3. data lakes are centralized repo for large amount and data. unstructured data.
4. uses aws glue for ETL.
5. for discovering, cleaning and transformation, ingestion
6. aws lake formation workflows/blueprints
   - contain complex multi-job etl activities.
7. access control
8. aws athena, quicksight, EMR, glue
9. use aws lake formation to ecntralize permission and access to your data lakes.
10. leverage column-level security when using aws quicksight.

### aws transfer family
1. managed service easily move in and out of s3 or efs.
2. supports SFTP, ftp over ssl, ftp, AS2.
3. includes scaling and HA.
4. pay for each endpt per hr and data transfers.
5. can only be used within vpc.
6. use cases: subscription-based data transfer, public data distribution, internal org data transfer, cms, erp.