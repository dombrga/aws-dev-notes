27. A company is launching a new application and will display application metrics on an Amazon CloudWatch dashboard. The company's product manager needs to access this dashboard periodically. The product manager does not have an AWS account. A solutions architect must provide access to the product manager by following the principle of least privilege.
Which solution will meet these requirements?

A. Share the dashboard from the CloudWatch console. Enter the product manager's email address, and complete the sharing steps. Provide a shareable link for the dashboard to the product manage.

28. A company is migrating applications to AWS. The applications are deployed in different accounts. The company manages the accounts centrally by using AWS Organizations. The company's security team needs a single sign-on (SSO) solution across all the company's accounts. The company must continue managing the users and groups in its on-premises self-managed Microsoft Active Directory.

    Which solution will meet these requirements?

    B. Enable AWS Single Sign-On (AWS SSO) from the AWS SSO console. Create a two-way forest trust to connect the company's self-managed Microsoft Active Directory with AWS SSO by using AWS Directory Service for Microsoft Active Directory.

    Explanation:
    AWS Single Sign-On (AWS SSO), now called AWS IAM Identity Center, provides centralized SSO access across multiple AWS accounts in AWS Organizations. To continue managing users and groups in the company's on-premises self-managed Microsoft Active Directory, the company can connect the directory to AWS Managed Microsoft AD by using a two-way forest trust. The two-way trust is required so IAM Identity Center can authenticate users and read users and groups from the self-managed Active Directory.

    Option A is incorrect because a one-way trust is not enough for IAM Identity Center in this scenario. Option C is incomplete because it creates the trust but does not configure AWS SSO/IAM Identity Center for SSO across accounts. Option D adds unnecessary operational overhead by deploying a separate on-premises identity provider.

33. A company runs an online marketplace web application on AWS. The application serves hundreds of thousands of users during peak hours. The company needs a scalable, near-real-time solution to share the details of millions of financial transactions with several other internal applications. Transactions also need to be processed to remove sensitive data before being stored in a document database for low-latency retrieval.
What should a solutions architect recommend to meet these requirements?

    C. Stream the transactions data into Amazon Kinesis Data Streams. Use AWS Lambda integration to remove sensitive data from every transaction and then store the transactions data in Amazon DynamoDB. Other applications can consume the transactions data off the Kinesis data stream.

    1. Real-time Data Stream: To share millions of financial transactions with other apps, you need to be able to ingest data in real-time, which is made possible by Amazon Kinesis Data Streams.
    2. Data Transformation: You can cleanse and eliminate sensitive data from transactions before storing them in Amazon DynamoDB by utilizing AWS Lambda with Kinesis Data Streams. This takes care of the requirement to handle sensitive data with care.
    3. Scalability: DynamoDB and Amazon Kinesis are both extremely scalable technologies that can manage enormous data volumes and adjust to the workload.

34. A company hosts its multi-tier applications on AWS. For compliance, governance, auditing, and security, the company must track configuration changes on its AWS resources and record a history of API calls made to these resources.
What should a solutions architect do to meet these requirements?

    B. Use AWS Config to track configuration changes and AWS CloudTrail to record API calls.

    AWS Config for Configuration Changes: AWS Config is a service that tracks changes to resource configurations over time. It provides a history of configuration changes to your AWS resources and helps with compliance and auditing by allowing you to assess how resource configurations have changed over time.

    AWS CloudTrail for API Calls: AWS CloudTrail is designed specifically for recording API calls made to AWS resources. It captures detailed information about who made each API call, the actions taken, and the resources affected. This is essential for auditing and security purposes.

36. A company is building an application in the AWS Cloud. The application will store data in Amazon S3 buckets in two AWS Regions. The company must use an AWS Key Management Service (AWS KMS) customer managed key to encrypt all data that is stored in the S3 buckets. The data in both S3 buckets must be encrypted and decrypted with the same KMS key. The data and the key must be stored in each of the two Regions.

    Which solution will meet these requirements with the LEAST operational overhead?

    B. Create a customer managed multi-Region KMS key. Create an S3 bucket in each Region. Configure replication between the S3 buckets. Configure the application to use the KMS key with client-side encryption.

    Explanation:
    The requirement says that the data in both S3 buckets must be encrypted and decrypted with the same KMS key, and that the key must exist in both AWS Regions. This points to an AWS KMS multi-Region customer managed key. A multi-Region KMS key has related keys in different Regions with the same key material, which allows data encrypted in one Region to be decrypted in another Region.

    Option A is incorrect because SSE-S3 uses Amazon S3 managed keys, not AWS KMS customer managed keys. Option C is incorrect because it creates customer managed KMS keys but then uses SSE-S3. Option D is close, but it creates separate KMS keys in each Region instead of using a multi-Region KMS key with the same key material.

47. A company needs guaranteed Amazon EC2 capacity in three specific Availability Zones in a specific AWS Region for an upcoming event that will last 1 week.
What should the company do to guarantee the EC2 capacity?

    D. Create an On-Demand Capacity Reservation that specifies the Region and three Availability Zones needed.

    An On-Demand Capacity Reservation is a type of Amazon EC2 reservation that enables you to create and manage reserved capacity on Amazon EC2. With an On-Demand Capacity Reservation, you can specify the Region and Availability Zones where you want to reserve capacity, and the number of EC2 instances you want to reserve. This allows you to guarantee capacity in specific Availability Zones in a specific Region.