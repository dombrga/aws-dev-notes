## amazon cloudwatch logs
1. allows to monitor, store, access log files from diff sources.
2. can query logs for investigation.
3. logs are encrypted by default. Can use kms.
4. some cw logs desti
   1. s3
   2. kds
   3. dfh
   4. lambda
   5. opensearch
5. 3 important terms
   1. **Log Event** - event in the record of actually happened within the app or aws svc.
      - contains timestamp and raw event msg, including custom logging event.
   2. **Log Stream** - collection of sequence of logs from same source. Think of as a continuous set of logs from a svc.
   3. **Log Group** - collection of log streams with same retention, monitoring, access control settings.
6. Log Retention
   - for log groups
   - expire after 1 day, 7 days or never expire.
7. some Log sources
   1. SDKs
   2. cw agent
   3. cw unified agent
   4. lambda funcs
   5. vpc flow logs
   6. aws api gw
   7. cloudtrail trails
   8. route 53 dns query logs
   9. elastic beanstalk
   10. ecs conts
   11. etc
8. there might be times you want logs to be sent to other destis. Use **amazon cw logs subscription**.
   - gives you realtime feed of log events from cw logs.
   - supports kds, lambda funcs, dfh, amazon opensearch svc
   - **filter patterns** filter which logs to deliver.
   - Log subscription filters can be set at acct level, or log grp level.
9. can export logs to s3.
   - for custom processing
   - bucket can be in the same acct or diff acct
   - export logs can take up to 12 hrs, not realtime.
10. **Log Groups are regional resources**.
