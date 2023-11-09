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
- The data in a local secondary index is organized by the same partition key as the base table, but with a different sort key.
- A query operation is used to search for an item using a primary key value. A scan operation reads every item in a table.
- Environment variables apply to AWS Lambda, not api gateway. Stage variables are name-value pairs that you can define as configuration attributes associated with a deployment stage of a REST API. They act like environment variables and can be used in your API setup and mapping templates.
- IAM roles are based on temporary security tokens, which are rotated automatically.
- Termination protection stack option can be enabled to prevent accidental deletion of an entire CloudFormation stack.
- Serverless approaches are ideal for applications where load can vary dynamically.
-  EC2 status checks and Elastic Load Balancing health checks can complete before the health check grace period expires.
-  PutMetricData is used to publish metric data points to CloudWatch. PutMetricAlarm can be used to create an alarm and associate it with a metric and threshold.