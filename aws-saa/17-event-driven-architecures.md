## amazon RDS events
1. near real-time notif containing info about events that occured on RDS instances.
2. do not contain DB data.
3. Categories
   1. db instance
   2. db snapshot
   3. db param grp
4. rds events can be configures to be sent to SNS topic, eventbridge. Then trigger lambda funcs.
5. examples
   1. db snapshot created
   2. db instance shutdown
   3. db cluster failover
6. can invoke lambda from rds postgres.
   - require iam permissions.