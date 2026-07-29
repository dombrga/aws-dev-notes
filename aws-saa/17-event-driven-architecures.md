## amazon RDS events
1. near real-time notif containing info about events that occured on RDS instances.
2. do not contain DB data.
3. Categories
   1. db instance
   2. db snapshot
   3. db param grp
4. rds events can be configures to be sent to SNS topic, eventbridge. Then trigger lambda funcs.
5. examples
   1. db snapshot created
   2. db instance shutdown
   3. db cluster failover
6. can invoke lambda from rds postgres.
   - require iam permissions.

## s3 events
1. S3 offers ability to receive notif when specific events happen.
2. supported destinations
   1. sns topic
   2. sqs queue
   3. lambda
   4. EventBridge
3. S3 event -> SQS queue -> lambda
4. s3 event -> sns. S3 can send events to sns.
5. Need to grant S3 permission to interact with sns, sqs, lambda, etc.
6. EventBridge - great choice for when you need to trigger workflows using other aws services, to support more destinations besides the ones before. Destinations like SageMaker Pipeline or aws batch.
   1. S3 -> amazon sagemaker.