chapter 5 serverless
SQS - simple queue service
sns - simple notif service

Lambda destinations
sqs, sns, lambda, event bridge

-when failed, 2 retries automatically
-dead letter queues- save failed invocation for further processing
-destinations - to send sucessful or unsuccessful invocations

Lambda deployment package - used to deploy your code to lambda
- console
- zip file archive - the deployment package. Contains app code and dependencies. 50mb limit
- you can create yourself
- if more than 50mb limit, must be zipped and uploaded to s3 first
- another way is lambda layers. Can reduce size of deployment package Multiple funcs can reference same layer 

- can only add memory directly. This will add cpu capacity. But you cannot add cpu capacity ONLY 
- default is 128mb, up to 10240gb
- STEPS: download code, configure, static initialization, function code
- execution env is temporary
- static init adds latency. To optimize: code, function package size, performance (of other services)
- importing libraries and sdks take time
- lambda destination provide more info when lambda function fails, DLQ just lets you know it failed
- only import whats needed on the sdk

5.21
- import api definition files. OpenAPI/swagger
- can use openapito create new api or update existing
- soap. api gateway as a soap web service passthrough. Or transform xml to json

5.22
- api gateway mock endpts. For create, test and debug. Mimics real response. Mock integration.
- you define status, response, etc

5.23
- api gateway stage. life cycle state of api (dev, prod, v3, etc). Can be on diff env
- different URLs
- stage variables, like env vars

5.25
- api gateway can transform http reqs and resps using parameter apping
-  req transfo include header, query string or request path
- res transfo include header or status code

5.26 and throttling
- api gateway caching. TTL is 300 secs default. api gateway returns cached resp
- throttling. default is 10k reqs/sec/region
- max concurrent is 5000reqs/region across all API. Request to increase
- 429 too many reqs error

5.27
x-ray - used to analyze and debug distributed applications. Visual represenation of app components. Latency, http status, errors
- integrates with many aws services like ec2, ecs, lambda, etc.
- can use xray w apps written in java, nodejs, .net, go, etc
- automatically captures metadata of api calls made to aws serviecs using aws sdk
- xray agent and xray sdk. Instrument your app to send data

5.28
- install xray daemon on ec2 of onprem server. Or on ec2 instance inside elastic beanstalk. Or in own docker container on ecs 
- annotation to send extra data

5.30
- serverless. Enables to build scalable apps without managing own servers. Event-driven. Pay only when code executes
- api gateway. Everything is logged to cloudwatch 
- lambda triggers. dynamodb, kinesis, etc

5.31
- lambda can access resource in a private vpc
-

5.32
- aws services are building blocks that can be integrated together to create an app.
- create loosely coupled. Operate and scale Independent of each other
- data storage for lambda /tmp ephemeral, lambda layer. S3 and efs