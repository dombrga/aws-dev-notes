## Decoupled architectures
### Tightly coupled archi
1. components heavily dependon each other.
2. If one is impacted by downtime, entire system is impacted.
3. Leverage synchronous system design. Components directly communicate with each other. Interact same time or realtime.

### Loosely coupled archi
1. can be more complex in the design.
2. components are less dependent on each, minimizing impact of changes or failure to each other.
3. Common methodology for decoupling architecture is by use of **messaging queue**.
4. Offers resiliency and asynchronous communication

### push and pull-based messaging
1. push (topic)
   - msg sent by producer to a server and immediately sent to consumer.
2. pull (queue)
   - msgs are sent by producer to a server (queue), get queued, and pulled off by a consumer.
3. SNS for push. SQS for pull.

## amazon sqs
1. msg queue svc for async processing of work.
2. to implement decoupled and distributed systems using diff queues.
3. A resource called producer sends a msg to an SQS queue, and anothe resource called consumer pulls it for processing.
4. To build a buffer between components. When producers produce msg faster consumption, msg can be queued and will be processed some time later.
5. Concepts
   1. send msg to queue via SendMessage api.
   2. poll and receive msg via ReceiveMessage api.
   3. DeleteMessage api after receiving and processing msg.
6. Commonly integrated with lambda func and api gw.
   - api gw is producer.
   - lambda is consumer.
7. If need durability, resiliency, availability, scalability, think SQS.
8. access control and secu
   1. use iam and access policies for controlling access to sqs queues.
   2. server side encryption to protect data in msgs. SSE-QS of kms.
   3. sqs is public svc. Important to implement correct iam policies and to restrict access via vpc endpts.
9. Best practice is to have separate queues for separate functions in a workflow.