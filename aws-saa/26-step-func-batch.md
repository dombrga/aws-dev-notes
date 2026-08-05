## aws step function
1. serverless orchestration svc for business app and workflows.
2. used to orchestrate lambda. Also sqs, api gw, etc.
3. capabilities
   1. allows retries
   2. parallel processing
   3. can require human approval
   4. built in error handling
4. use cases
   1. data processing workloads - image and video proce, etl, batch
   2. order processing
   3. security automation with human approval

### Components
1. state machines (workflows)
   - series of event-driven steps made up of different tasks and flows
2. task states
   - belongs to state machines
   - unit of work
3. Some states
   1. Pass - passes any input directly to its output
   2. Task - single unit of work performed
   3. Choice - adds branching logic to state machines
   4. Wait - time delay
   5. Parallel - run parallel branches of execution
   6. Map
   7. Succeed
   8. Fail
4. Map states 2 modes
   1. inline mode - default mode with limited concurrency
   2. distributed mode - for large scale processing workloads.
5. workflow types
   1. standard
      - exactly once execution
      - run up to 1 yr
      - useful for long-running, auditable workflows
      - billed on # of transitions
   2. express
      - at least once and at most once execution
      - run up to 5 mins.
      - high event rate workloads
      - billed on # of executions, total duration, memory consumed.

## aws batch
1. fully managed batch processing svc.
2. run batch computing workloads on ec2 (ondemand, spot), ecs/fargate.
3. auto launches required compute.
4. submit jobs as needed, or schedule them.

### concepts
1. Jobs - unit of work submitted to aws batch.
   1. shell scripts
   2. exec
   3. docker images
2. job definitions - specifies how jobs are to be run.
3. Job queues - jobs get submitted to specific queues.
4. compute environment
5. Managed compute env
   1. aws manages capacity and instance types
   2. compute resources specs are defined
   3. launched into vpc subnets
   4. leverage fargate, fargate spot, spot
6. Unmanaged compute env
   1. you manage
   2. meet ecs ami specs
   3. less common
### compute env
1. fargate
   1. recommended for most workloads
   2. for fast start times
2. ec2
   1. need control over instance selection
   2. custom ami