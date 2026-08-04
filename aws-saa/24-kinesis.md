## amazon kinesis
1. allows you to ingest, process, analyze real-time streaming data and video.
2. like a huge data highway connected to your aws acct.
3. polling-based/pull-based
4. 4 important versions
   1. kinesis data streams
   2. data fire hose
   3. kinesis data analytics for sql applications
   4. kinesis video streams
5. For realtime or near realtime streaming.

## amazon kinesis data streams (kds)
1. **realtime streaming** of incoming data.
2. apps called consumers read data records from the streams.
3. perfect for large amounts of fast data ingestion.
4. typically takes <1 sec for data to be pulled off a stream.

### Concepts
1. Producers are the one pushing data to kinesis data streams.
2. Consumers (apps) processes the stream data in realtime.
3. Kinesis data streams contain shards, which what hold your data. Contains sequenced **data records**.
4. Data records are unit of data. 1 mb in size.
5. **Retention period** - configurable amount of time data records are available after being added to the stream. default 24 hrs, max 365 days.
6. **Shard** - streams are made up of 1 or more shards that have set amount of capacity. 5 read/sec or 2mb/sec reading. Writing 1000 writes/sec or 1mb/sec.
   - you create shards.
7. Ordering - partition keys are required when adding data to stream.
8. Replay - msgs do not go away until they expire, even when they get consumed. Allows for multiple consumers to replay same data records in same order.
9.  supports encryption within data streams using aws kms keys.
10. ![data streams archi sample](./images/24/data-stream-archi.png)

### producing and consuming data
1. Producers will use amazon kinesis producer library (KPL).
   - meant to make ingesting data simpler
   - handles aggregation, metric collection, retries.
   - not same as kinesis data streams api.
   - perfect for ec2 writing thousands of events/sec.
2. Consumers will use kinesis client library (KCL).
   - standalone java lib.
   - simplify consuming and proce data from kds.
   - offers load balancing across multiple workers, handles failures, responds to changes in # of shards, etc.
3. aws sdk for java is less popular option.
4. Enhanced Fan-out
   - makes kds push-based.
   - allows data to immediately get pushed to all consumers once it is ready on the data stream.
   - high performance.
   - incur addtl cost.
   - **to scale consumers of kds.**