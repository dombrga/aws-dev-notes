## lambda
1. Serverless - focus on code and leave mngmt of compute to others.
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

## lambda config
1. Concepts
   1. Runtime - language-specific env where code will run.
   2. IAM execution role - needed so lambda can make AWS api calls.
   3. Networking - optionally define VPC.
   4. Function Resources - define amount of memory
2. Runtimes
   - meant to relay invocation events or triggers, context info, responses
   - python, java, .net, golang, ruby, node
   - custom runtime - can create one.
3. Lambda compute and storage config options
   - default quota of 1000 concurrent executions per Region.
   - memory - 128 mb to 10240 mb.
   - env vars can be used
   - access to /tmp directory, can be 512 mb - 10240 mb. You get billed.
   - integration with EFS. For shared filesystem.

## lambda networking
1. By default, lambda func are deployed to aws-owned vpc that allows internet access.
2. You can allow traffic from lambda to other private aws svcs by using Lambda sec grps.
3. If you want private subnet Lambda to access internet, you can deploy and use NAT in a public subnet.

## lambda concurrency
1. Provisioned concurrency
   - \# of pre-initialized execution env allocated to your func.
   - useful for reducing cold start.
2. Reserved concurrency
   - max # of concurrent instances
3. Throttling - function will drop request and fail if it ran out of concurrency.

## lambda snapstart
1. provides as low as sub-second startup perf with no code changes.
2. java 11+, python 3.12+, .net 8+.
3. Lambda lifecycle
   1. Init - start extensions, bootstraps runtime, run static code
   2. Invoke
   3. Shutdown

## important lambda features
1. lambda version
   - publish copies of function
   - includes version's code, runtime, archi memory, layers and most config settings.
   - $LATEST. the current unpublished version.
2. lambda aliases
   - alias for easy reference
   - pointer to a function version
   - easily update aliases
   - Canary testing. Allow to implement traffic splitting.
3. Lambda layers
   - zip file that contains supplementary code or data.
   - to share common code or deps across lambda funcs.
   - reduce size of deployment packages.
   - easily share to other aws accts.