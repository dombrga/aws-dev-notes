AWS exam readiness

2. dynamodb offers conditional writes.
5. 50:1
7. VPC isu sed 
9. aws elasticache is not a supported destination for aws kinesis data firehose 

lambda layer - zip fil containing lib deps, custom runtime, etc

dymamodb streams - time ordered sequence of modifications in dynamodb for past 24 hrs

Transform - section in SAM for cloudformation

Handler - SAM template property. Lambda function code execution begins

- use eventbridge or CloudWatch Events to trigger lambda function after every specific time

- set DeletionPolicy to Retain in cf

- IAM user is not associated with ec2 instance. Policy, instance roles and 
permissions

- athena can be used to run sql on data on s3
- envelope encryption. encrypting data key with another key
- use iam instance role to grant access to ec2 instances
- cf change sets to notify if any resources will be deleted or updated
- cloudwatch does not provide average latency bet app services
- subnet is a range of IP addrs in VPC
- The data in a local secondary index is organized by the same partition key as the base table, but with a different sort key. GSI has different partition and sort key from the orig table
- A query operation is used to search for an item using a primary key value. A scan operation reads every item in a table.
- Environment variables apply to AWS Lambda, not api gateway. Stage variables are name-value pairs that you can define as configuration attributes associated with a deployment stage of a REST API. They act like environment variables and can be used in your API setup and mapping templates.
- IAM roles are based on temporary security tokens, which are rotated automatically.
- Termination protection stack option can be enabled to prevent accidental deletion of an entire CloudFormation stack.
- Serverless approaches are ideal for applications where load can vary dynamically.
- EC2 status checks and Elastic Load Balancing health checks can complete before the health check grace period expires.
-  PutMetricData is used to publish metric data points to CloudWatch. PutMetricAlarm can be used to create an alarm and associate it with a metric and threshold.
-  namespace is a container in cloudwatch metrics . EC2 uses aws/ec2 namespace. it cannot be used to filter results to show the metrics of a speci env
- dimension in cw metrics is like a filter.
- security group is like a firewall that controls inbound/outbound traffic.
- in cf template, DeletionPolicy to Retain to prevent accidental deletion of RESOURCE. Set stack termination protection to Enable for WHOLE STACK.
- AWSLambdaBasicExecutionRole grants permission to upload to cw, not to s3. Lambda func execution role is an iam role that grants the func to access aws services and resources.
- route53 is dns service. clouffront is a cdn service
- app load balancer supports path-based routing. Application Load Balancer supports sticky sessions, enabling stateful applications.
- deploy ssl certs to load balancer
- sort keys can filtered through range queries like >, <, begins_with, between
- sse-kms supports automatic key rotation for s3
- synchronous express workflow can handle errors and retries and execute parallel tasks without additional code
- create-stack command creates a stack as specified in the template provided.
- codebuild natively supports cw events. sns integrates with cw
- eventbridge can be used to trigger Lambda based on cw metrics. pullRequestCreated and pullRequestSourceBranchUpdated events
- read replicas are not a feature of dynamodb. Using DAX is the recommended approach to reducing response times for read-intensive applications, applications that read a few items frequently, and applications that perform repeated reads against a large set of data.
- BatchGetItem to retrieve multiple specific items with single api call, minimum impact to db
- Scan get all items in dynamodb
- aws athena lets you query data stored in s3. interactive query service. also serverless
- you must use X-Forwarded-For headers to capture client IP addresses
- aws elasticache for memcached scales horizontally. not recommended for real-time
- for more performant Lambda, establish your database connections from within the Lambda execution environment to enable connection reuse.
- viewer policy in cloudfront
- ElastiCache is a great option for storing session data.
- SQS is an AWS-managed message queuing service that allows you to decouple and scale microservices, distributed systems, and serverless applications.
- You will need to enable the function to connect to the VPC by providing the correct subnet and security group needed to access the RDS instance.
- lambda layers is like a separate folder from the dep package that contains libraries the Lambda uses. Lambda deployment package should be as small as possible
- EFS is a good option for storing persistent files because it enables sharing, dynamic updates, and is persistent storage.'
- By using Parameter Store to store any secrets as a SecureString, the secrets are encrypted and not stored in plain text.
- Pre Signed urls are used when we need to give access to an object in s3 securely to viewers who don't have AWS credentials. Signed urls / cookies are used to restrict access to the files in cloudfront edge caches and s3 for authenticated users and subscribers.
- A status of ALARM indicates that the metric or expression is outside the defined threshold.
- aws xray can also be used for Lambda.
- CloudWatch cannot be used to identify performance issues in distributed serverless applications.
- qualified arn is ARN plus version suffix. unqualified ARN is ARN without version suff
- use aws Encryption SDK to encrypt files in client side
- cloudtrail data is stored in s3. Athena
- sqs delay queue lets you postpone delivery of messages to the queue
- always check which data is needed. Operation system metric does not include application-specific logs
- cw does not record latency and info about incoming/outgoing http reqs
- xray daemon needs xray sdk to upload trace data to xray
- xray service map has latency and any failues
- cloudformation nested stacks to reuse or base a stack from a given stack.
- ensure AMIs are available in the region you want when launching ec2 to multiple regions
- PutMetricData to send custom metric data to cw
- ss3-kms for s3 
- dynamodb query operation uses primary key
- buildspec and codebuild env variables are used by codebuild
- appspec file is used by codedeploy
- Export in Output section and Fn::ImportValue in cf for share details between cf templates
- parallel scan and reducing page size to speed up dynamodb scan ops
- Parameters section of cf is used for passing input values
- While versioning in S3 is useful for data protection and archival, it's not a requirement for hosting a static website.
- CloudWatch can send a notification to an SNS topic
- cw logs to interactively search and analyze log data
- aws sdk for javascript for retry and backoff