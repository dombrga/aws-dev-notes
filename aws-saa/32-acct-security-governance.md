# aws cloud trail
1. svc that increases visibility and governance of aws resources by recording user and resource activity.
2. records aws management console actions and api calls.
3. enabled by default, cannot be turned off.
4. allows for
   1. incident investigation
   2. near real time detection of api calls
   3. helps maintain regulatory compliances
5. what does it record?
   1. aws mngmt console actions, even login
   2. aws cli calls
   3. aws service actions
   4. aws sdk api calls
6. CloudTrail event
   - record of an activity in an aws acct, providing historical trails
7. ct event types
   1. **management events** - info about mngmt operations. For example, TerminateInstance ec2 api call.
   2. **data events** - info about operations on resource. Tends to be high volume. Example is s3 GetObject
   3. **Insights events** - capture unusual api call/errors rates in your aws accts
8. Event retention
   - up to 90 days before removal
   - can be customized using cw and s3

# cloudtrail trails
1. Trails
   - config or resource you want to record events of.
2. regional resources. Captures events in respective region.
3. supports multi region deployment.
4. customize delivery of logs for long term storage in cw and s3.
5. trigger rules on events using EventBridge.
6. encryption using kms.
7. can set up SNS notif for log file updates, for example in s3.
8. **Organizational trail**
   - configure delivery of ct events in the mngmt acct and member accts in an org to same s3, cw logs, and eventbridge.
9. Log file valida tion
   - feature to help determine whether log file was modified, delete or unchanged after ct delivered it to the destination.
10. get one free trail per region.
11. exam scenario
    - ![cloudtrail-scenario](./images/32/ct-scenario.png)
