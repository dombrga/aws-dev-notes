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