https://www.examtopics.com/exams/amazon/aws-certified-developer-associate-dva-c02/view/1/


#4 aws step functions can be used for creating workflow of functions and has error handling features. Lambda can be used in step funcs

#5 something to do with permissions
#6 AllowedValues in clouf formation template

#10 aws parameter store

#14 s3 object lambda. Add your own code to S3 GET, HEAD, and LIST requests to modify and process data as it is returned to an application

#15 use function alias

#17 aws code deploy in-place deployment. ApplicationStop -> BeforeInstall -> AfterInstall -> ApplicationStart

#23 s3 is highly scalable and durable. Using the network shared folder can be a single point of failure

#24 AWS Amplify is a fully managed service that allows developers to build and deploy web applications and static websites.

#25 read replicas for read-heavy workload. Multi-az is for disaster recovery

#26 B persisdent storage, but not relational.

#27 A. you cannot encrypt an existing unencrypted. Create new ami and encrypt it

#29 AC. ProvisionedThroughputExceededException. Implement expo backoff or reduce freq/size of reqs

#31 B. PutObject API is called. You can put key in x-amz-server-side-encryption header

#32 B. aws cloudformation is a service to easily model, provision and manage aws and 3rd party resources

#34 C. The recommended AWS service for defining serverless resources in YAML is the AWS Serverless Application Model (AWS SAM).

#35 B.  Configure an S3 event to invoke an AWS Lambda function that inserts records into DynamoDB.

#36 AB. Add a CloudFormation Deletion Policy attribute with the Retain value to the database resource. 
 Update the CloudFormation stack policy to prevent updates to the database

#37 A. Define a resource-based policy on the S3 bucket to deny access when a request meets the condition “aws:SecureTransport”: “false”

#38 D. Update the S3 bucket policy by including the S3:ListBucket permission and by setting the Principal element to specify the account number of the EC2 instance.
Option D is not the most secure choice, as utilizing bucket policies and specifying account numbers can potentially lead to overly complex and less secure configurations, especially if not managed carefully.

#39 C. AWS Systems Manager Parameter Store SecureString parameters 

#40 A. Create the Lambda function. Configure VPC1 access for the function. Attach a security group named SG1 to both the Lambda function and the database. Configure the security group inbound and outbound rules to allow TCP traffic on Port 3306.

#41 BD. IntegrationLatency and Latency

#43 A. /tmp dir. If Lambda func creates files <10mb during invocation but only temporary

#44 B. Lambda layer to reduce size of dep package

#45 A. get id from context object

#46 C. Enabling DynamoDB Streams on the table allows you to capture and process changes (inserts, updates, deletes) to the table in real-time.

#47 AE. Use EC2 Image Builder to create an Amazon Machine Image (AMI). Install all the patches and agents that are needed to manage and run the application. Update the Auto Scaling group launch configuration to use the AMI.
Remove any commands that perform operating system patching from the UserData script

#48 C. Store the credentials in AWS Secrets Manager. Set the secret type to Credentials for Amazon RDS database. Select the database that the secret will access. Use the default AWS Key Management Service (AWS KMS) key to encrypt the secret. Enable automatic rotation for the secret. Use the secret from Secrets Manager on the Lambda function to connect to the database.
When talking about credential rotation and secure storage, THINK aws secrets manager. 
KMS is for encrypt/decrypt

#50 D. Use a request mapping template to select the mock integration response

#51 B

#52 A. Implement Kinesis Data Firehose data transformation as an AWS Lambda function. Configure the function to remove the customer identifiers. Set an Amazon S3 bucket as the destination of the delivery stream.

#53 A. Set the image resize Lambda function as a destination of the avatar generator Lambda function for the events that fail processing.

#56 A. Increase the number of shards of the Kinesis data stream. 
C. Increase the memory that is allocated to the Lambda function.

#57 B. Create a new CodePipeline stage that occurs after the container image is built. Configure ECR basic image scanning to scan on image push. Use an AWS Lambda function as the action provider. Configure the Lambda function to check the scan results and to fail the pipeline if there are findings.

#58 A. Add a second cache behavior to the distribution with the same origin as the default cache behavior. Set the path pattern for the second cache behavior to the path of the login page, and make viewer access unrestricted. Keep the default cache behavior's settings unchanged.

#59 C. Add a test phase to the amplify.yml build settings for the application.

#60 B. Create and inspect the Lambda dead-letter queue. Troubleshoot the failed functions. Reprocess the events. 

#61 dynamodb max row size is 400kb
B. Generate the reports and then store the reports in an Amazon S3 bucket that uses server-side encryption. Attach the reports to an Amazon Simple Notification Service (Amazon SNS) message. Subscribe the customer to email notifications from Amazon SNS.

#62 
C. Change the deployment policy to rolling with additional batch. Specify a batch size of 1.

#63
A. Manually instrument the X-Ray SDK in the application code.

#64
D. Configure the VPC, subnets, and a security group for the Lambda functions.

#65
A. Create a Lambda environment variable to store the table name. Use the standard method for the programming language to retrieve the variable.

#66
B. Use Amazon RDS Proxy to create a proxy that connects to the DB instance. Update the Lambda function to connect to the proxy.

#67
B. Store the smart meter readings in an Amazon DynamoDB table. Create a composite key by using the location ID and timestamp columns. Use the columns to filter on the customers' data.

#68
B. Create the test events. Configure the event sharing settings to make the test events shareable.

#69
B. Create an AWS CodeBuild project. Add the repository package's build and test commands to the project's buildspec.
E. Add a new stage to the pipeline after the source stage. Add an action to the new stage. Specify the newly created project as the action provider. Specify the source artifact as the action's input artifact.

#70
A. Add an override to the feature. Set the identifier of the override to the engineer's user ID. Set the variation to Variation A.

#71
A. Create a global secondary index (GSI) with productFamily as the partition key and productType as the sort key.
- You cannot create local secondary index on an already created table, but you can create global secondary index

#72
B. Redeploy the Lambda function in the same subnet as the RDS instance. Ensure that the RDS security group allows traffic from the Lambda function.
- aws resources outside 

#73
C. Use Amazon CloudWatch Logs to create a metric filter that has a filter pattern for DECRYP_ERROR. Create a CloudWatch alarm on this metric for a threshold >=1. Configure the alarm to send Amazon Simple Notification Service (Amazon SNS) notifications.

#74
B. Modify the function to store the values in Amazon ElastiCache. When the function initializes, use the previous values from the cache to calculate the rolling average.

#75
C. pullrequestsourcebranchupdated, pullrequestcreated

#76
A. Query the instance metadata from http://169.254.169.254/latest/meta-data/.

#77
C. Use the KMS GenerateDataKey API to get a data key. Encrypt the data with the data key. Store the encrypted data key and data.

#78
A. Use an Application Load Balancer and the X-Forwarded-For headers.
- http/https listeners
- x-forwarded-for header

#79
B. CloudWatch Logs only publishes metric data for events that happen after the filter is created.

#80
A. CodeDeployDefault.ECSCanary10Percent15Minutes
- ecscanary. Shifts 10% of traffic to new instance. After 15 mins, shift remaining traffic to new instance

#81
C. Configure the Amazon CloudWatch agent to track the memory usage of the instances.

#82
B. Set up the Lambda function with a role and key policy to access an AWS KMS key. Use the key to generate a data key used to encrypt all data prior to writing to /tmp storage. 

#83
B. The resource-based policy for the Lambda function does not have the required permissions to be invoked by Amazon S3.
- s3 event notif can be activated for files >1000mb
- Lambda can be invoked directly from s3 events
- s3 not neces need to be public

#85
B. Update the Lambda function in the API Gateway API integration request to use the hotfix alias. Deploy the API Gateway API to a new stage named hotfix. Test the backend. 
D. Modify the Lambda function by fixing the code. Test the Lambda function. When the Lambda function is working as expected, publish the Lambda function as a new version. Create the alias hotfix. Point the alias to the new version. 