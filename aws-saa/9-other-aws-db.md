### aws documentDB
1. managed mongodb service.
2. storage volume grows as data grows, up to 128 Tib in 10 gb increments.
3. infrastructure similar to aurora.
4. cluster
   1. instance-based
   2. elastic - supports millions of reads/writes per sec
5. deploy in to vpc

### amazon neptune
1. graphdb - stores nodes and relationships, instead of table or docs.
2. for social networks, recommendations engines, knowledge base/ graphs (like wikipedia), useful for fraud detection platform.
3. aws neptune is fast, fully managed graph db service.
   - optimized for storing billions of relationships.
   - ms of latency.
   - supports apache tinkerpop gremlin, neo4j opencypher , sparql
   - offers HA with read-replica and replication across 3 AZs.
   - PITR and continuous backup.
   - uses: build conn bet identities; security graphs to improve IT sec.
   - neptune streams: every change in the graph is logged in order, no duplicates.

### aws keyspaces (apache cassandra)
1. cassandra
   - distributed DB that uses nosql.
   - primarily used for big data solutions.
   - used by netflix.
2. managed apache cassandra-compatible db service.
   - provisioning, patching, managing server.
   - installing, maintaining,
   - serverless service, pay only what you use.
   - table auto scale up and down.
   - thousands of req/sec.
   - cassandra query language (CQL)
   - some iot workloads.

### amazon quantum ledger db (qldb)
1. ledger db
   - nosql db that is immutable, transparent and has a cryptographically verifiable transaction owned by one authority.
   - you cannot replace old content in a ledger. Instead add new record.
   - used for cryptocurrency, shipping company to track items, boxes; pharma comp to track creation and distri of drugs.
2. QLDB
   - managed aws ledger db service.
   - centralized component for logging transactions.
   - not to be confused with aws managed blockchain.
   - PartiQL queries.
   - use cases. store financial transactions; supply chain systems for recording history of each transaction, provide details of every batch manufactured, shipped, stored, sold; maintain claims history

### aws timestream
1. serverless db for time series data and LiveAnalytics data.
2. store trillions of time series data pts/day and analyze quickly.
3. keeps recent data in memory and moves historical to cost optimized storage tier.
4. integrates with
   1. aws iot core.
   2. aws msk
   3. aws kinesis
   4. aws quicksight
   5. grafana/prometheus
   6. aws sagemaker.
5. use cases
   1. iot sensors
   2. app performance monitoring
   3. financial trading and market data analysis.