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