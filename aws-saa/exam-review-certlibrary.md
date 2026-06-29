1. A. Use AWS Config rules to define and detect resources that are not properly tagged.
2. B. Create an Amazon S3 bucket and host the website there.
3. C. Stream the transactions data into Amazon Kinesis Data Streams. Use AWS Lambda integration to remove sensitive data from every transaction and then store the transactions data in Amazon DynamoDB. Other applications can consume the transactions data off the Kinesis data stream.
4. B. Use AWS Config to track configuration changes and AWS CloudTrail to record API calls.
5. A company is preparing to launch a public-facing web application in the AWS Cloud. The architecture consists of Amazon EC2 instances within a VPC behind an Elastic Load Balancer (ELB). A third-party service is used for the DNS. The company's solutions architect must recommend a solution to detect and protect against large-scale DDoS attacks.
Which solution meets these requirements?

D. Enable AWS Shield Advanced and assign the ELB to it.

6. B. Create a customer managed multi-Region KMS key. Create an S3 bucket in each Region. Configure replication between the S3 buckets. Configure the application to use the KMS key with client-side encryption.
7. B. Attach the appropriate IAM role to each existing instance and new instance. Use AWS Systems Manager Session Manager to establish a remote SSH session.
8. C. Add an Amazon CloudFront distribution in front of the S3 bucket. Edit the Route 53 entries to point to the CloudFront distribution.



1.  B. Create an Amazon AppFlow flow to transfer data between each SaaS source and the S3 bucket. Configure an S3 event notification to send events to an Amazon Simple Notification Service (Amazon SNS) topic when the upload to the S3 bucket is complete.

AppFlow is a fully managed AWS service built specifically for transferring data between SaaS applications and AWS services like S3.
	12. C. Deploy a gateway VPC endpoint for Amazon S3.
	13. B. Establish a new AWS Direct Connect connection and direct backup traffic through this new connection.

