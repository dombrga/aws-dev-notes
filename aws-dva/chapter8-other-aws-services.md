chapter 8 other aws services
8.1 
- sqs. pull based. Standard queue and FIFO queue
- standard. Best effort ordering. Message are delivered at least once, occasional duplicates
- fifo. message order is preserved. Messa is delivered once. No dups. Good for banking tx
- 1-14 days retention period, default 4 days

8.2 other aws services
- sqs. Distributed message queueing system

8.3 sqs settings
- visibility timeout - amount of time that the message is invisible in the sqs queue after a reader picks up the message. 
- once reader pulls the message, the timeout starts (30secs default). Ideally the time to finish the job. After, message is deleted from the queue
- if job is not processed within this time, the message will be visible again and another reader will process it
- visib timeout can be changed. Up to 12 hrs
- short polling. Returns a response immediately even if the message q being polled is empty. Will for these responses
- long polling. Periodically polls the q. Does not return res until messa arrives in the messa q or long poll times out. Saves money. Generally pref
- ChangeMessageVisibility API for extending lenght of time to process jobs

8.4 
- sqs delay queues. Postpone delivery of new messages to a queue for some time.
- standard queues. Mssgs already in the queue are not effected, only new mssgs
- fifo qs, affects mssgs already in the q
- when to use? May be needed for Large distri apps
- default is 0 secs, max is 900secs
- s3 can be used for managing large sqs mssgs, 256kb-2gb. Needs sqs xtended client lib and aws sdk for java. Cant use aws cli, aws management console/sqs console, sqs api

8.6 sns
- simple notif service. Set up, operate and sent notifs from the cloud.
- like push notifs, to send sms and email to sqs or any http endpt, to trigger Lambda funcs, publish to another sns topic, send to another aws service
- pub-sub, publish-subscribe model. Apps can publish or push to a TOPIC. Subs can receive from a topic
- topic is an access point that recipients subscribe to and receive identical copies.
- sns formats copies
- sns are stored durably, across multiple AZ
- instantaneous, push-based, simple api, inexpensive, easy to configure, point and click interface, multiple protocols
- sqs and sns are messaging service.

8.7 sns vs ses
- ses, simple email service. For sending emails to customers using pay-as-u-go model. Needs only email address to send. Not subscription based
- send and receive emails with incoming mails delivered to s3 bucket
- trigger Lambda and sns
- use ses: automated emails, online purchases, marketing emails
- sns: sms, http, sqs, email. Fanout messages to large # of recipients, replicate and push messgs to multiple endpts nad formats. Consumers need to subscribe to topic before receiving notifs

8.8 kinesis
- family of services to collect, process, and analyze streaming data
4 core services
- kinesis streams: data streams and video streams. Build custom apps that process data in real time. Can be saved to aws data stores
- kinesis data firehose. Capture, transform, and load data streams to aws data stores for real-time analytics. Then BI tools can be used for real time analysis of the stored data
- kinesis data analytics. Analyze, query, transform data in real time using standard sql.
- Kinesis streams retain data by default for 24hrs, max of 365 days. Stored in shards, sequence of data records. Shards are only for kinesis streams and has fixed unit of capacity.
Each record in the stream has unique sequence number, order is maintained
-  kinesis video stream. Stream video from conneced devices to aws. Can be used for analytics and ml
- kinesis data firehose. No sharding, capacity is automated. Does not need the data to be consumed. No data retention. Processed data can be stored in aws data stores. Near real time
- kinesis data analytics. To run sql queries in kinesis streams and firehose, and stores result in s3, redshift, opensearch, etc aws data stores
- as data rate increases, increase # of shards (resharding)
- kinesis client library. Runs on consumer instance. Tracks # of shards in stream. Discover new shard. Load balances between consumers.
- generally, #of consumers should no exceed # of shards (except for failure or standby purposes)
- cpu utilization should determine # of consumer instances, not # of shards. Use auto scaling group
- cloudformation. panggawa automatic ng aws services

8.11 elastic beanstalk (eb)

- eb. Deploy ang scale web apps without provisioning ec2. Focus on writing code and not worry about infrastracture. Provide code to eb. Eb will provision load balancers, ec2 etc. Integrates with cloudwatch and cloudtrail. Has health dashboard.
- java php python ruby go .net node. Managed platforms like tomcat and docker.
- provisions infra, load bal, auto scaling and app health monitoring. Installation and management of app stack. You have admin control of aws resources
- devs dont need to be sysad
- get apps to market faster. Fastest and simplest way to deploy apps to aws
- Elas bea is free to use, you only pay for the resources you deploy using it. 

8.12  4 ways of updating apps in elastic beanstalk
- all at once. Deploys to all hosts concurrently. Will experience outage, not ideal for mission-critical
- rolling. Deploys new versions in batches. Wont experience outage. Each batch will be taken out while deployment, so capacity will be reduced. Not ideal for performance sensitive system
- rolling with additional batch. Launches additional batch of instances, then performs rolling. Maintains full capacity during deployment
- immutable. Deploys new version to new group of instances before deleting old instances after passing health checks
- traffic splitting. Installs new version on new set instance. Forwards % of client traffic to new app for evaluation. Enables canary testing. If new instances stay healthy, 100% traffic will be forwarded to them

8.15 customizing elastic beanstalk env
- there are many ways
- config is different for amazon linux 1 and 2
- pre-amazon linux 2. Config file in yaml o json, has .config extensions inside .ebextensions folder. This defines packages to insstall, create linux users and grps, etc.
- amazon linux 2. Buildfile, procfile, platform hooks.
- buildfile. commands that run for short periods, and exit after. In root dir 
- procfile. long running apps processes. In root dir. Run continuously. Mointors and restarts processes that terminate
- platform hooks. Custom scripts of exe files that elas bean to run at chosen stage of ec2 provi process. Stored in dir in app source code. .platform/hooks/rebuild, predeploy, postdeploy

8.16 integrating rds with elas bea
- 2 ways, inside or outside.
- inside. Quick and easy to get started. Launch rds within elas bea console. Terminate the env also terminates db. Not good for PROD.
- outside. Dont use elas bea to create rds db. Use rds console or aws cli. You can terminate elas env without terminating db. Good for prod, more flexibility
Connecting to outside db
1. additional secu grp to be added in env's auto scaling grp
2. connection string/amazon resource name info to app server in elas bea env properties

8.17 migrating apps to elas bea
- windows web application migration assistant/.net migration assistant for beanstalk. For migrating .net app or entire website from windows servers to elas bea env
- this is open source