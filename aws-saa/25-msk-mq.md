## amazon managed streaming for kafka (msk)
1. managed svc for running data streaming apps that leverage apache kafka.
2. Control plane. create, update, delete clusters.
3. deploy clusters in vpc across multi AZs.
4. alternative to amazon kinesis.
5. Recovery
6. supports encryption.
7. msk serverless.
8. Common consumers
   1. ec2
   2. ecs
   3. eks
   4. kinesis data analytics
   5. aws glue

## amazon mq
1. message broker service for easier migration of existing app to aws.
2. supports
   1. apache activeMQ
   2. rabbitMQ
3. if creating new app, consider SNS and SQS.
4. HA archi.
5. MQ broker engine types
   1. amazon mq for activemq - active/standby deployments
6. **Exam tip:** JMS or other mssging protocol like amqp 091, amqp, mqtt, openwire, stomp, think amazon mq.