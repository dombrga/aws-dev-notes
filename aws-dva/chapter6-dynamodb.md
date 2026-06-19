dynamodb
6.1
- dynamodb. fast and flexible nosql db. 
- consistent, single-digit ms latency
- key-value. doc formats supported are json, html, and xml
- mobile, web, gaming, ad tech, iot, etc
- serverless. Integrates well with lambda. Auto scale
- stored in ssd. Spead 3 geo distinc data center
- consistent reads. Takes around 1 sec for writes to reflect. Eventually and strongly consistent.
- dynamodb tx (acid). All or nothing operation.
- each row or record is called item
- primary key. 2 types, partition and composite key (partition key + sort key)
- partition key. Unique attr
- sort key could be timestamp, date, etc
- all items with same partition key are stored together

6.2
- authentication and access control using IAM
- permissions, roles
- restrict user access. Users cannot access other user's data. dynamodb:LeadingKeys
- fine-grained access control with iam

6.4
- secondary index. More flexible querying, not necessarily primary key. Global and local 2ndary index. Querying on specific columns
- 

6.6
query - finds items based on prim key and a distinct value. Returns all attribs. Use ProjectionExpression to return specific attribs
- use sort key to refine results. Results are sorted by sort key, asc order. ScanIndexForward to false to reverse
scan - examines every item. Returns all attribs bdef. Returns all item, then put a filter 
 - query is more efficient.

6.8
- when creating table, you can specify reqs of read and write capacity
- 1 x 1kb w/s. 1 strong consistent read of 4kb/s or 2 eventually consistent  of 4kb/sec (def)
- parallel scan is possible. Beware of it
- isolate scan to specific table
- improving perf. Set smaller page size

6.9
on-demand capa. Unknown workloads, unpredictable traffic, spiky peak. Hard to predict cost
provisioned capa. Predictable

6.10
dynamodb accelerator. Fully managed, clusterd in-memory cache for dynamodb
- allows to point dynamodb api to dax cluster
- eventually consistent cache hit

6.12 dynamodb stream
-  Time ordered sequence of item-level mods (insert, update, delete). 
- encrypted at rest and stored for 24hrs.
- has dedicated endpoint
- for audit or archive tx. As lambda event source

6.13
- ProvisionedThrooughputExceeded Exception - request rate is too high for the r/w capacity 
- sdk will auto retry reqs until success
- if not sdk, reduce req frequency or use exponential backoff
- expo backoff is using retry. Waiting longer than the last retry before retrying again. Starting retrying than the last retry