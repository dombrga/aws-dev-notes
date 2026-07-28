## lambda
1. Serverless - focus on code and leave mngmt of compute to otherss
   - ease of use
   - event based. Respond to an event.
2. AWS Lambda
   - run code as virtual functions
   - no provision of server needed, handled for you.
   - can run for up 900 secs or 15 mins.
   - scaling is handled for you.
3. lambda features and benefits
   - free tier of 1mil req and 400k gb compute per month.
   - integrates with s3, dynamodb, eventbridge, sqs/sns.
   - logging and monitoring in amazon cw.
   - run in aws-owned vpc, allows internet access.
   - easily scale your compute power as required.
4. how to deploy lambda
   1. By console. Upload code and deps.
   2. zip file. up to 50mb in compressed size. Can be stored in s3 if size is bigger.
   3. Container image - build image locally, upload to ecr, them lambda pulls it. For very heavy dependencies use case. Not typical.
5. Trigger - resource or config that invokes lambda.
6. Event source mapping - lambda resources for reading items from streams and queues.

##