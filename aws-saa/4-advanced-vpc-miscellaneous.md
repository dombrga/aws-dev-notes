## June 24, 2026

1. block bad IPs by NACL so you dont modify sec grp. this is quickest and most cost-effective.

### VPC flow logs.
1. captures and monitor IP traffic info going to and from vpc.
2. 3 source options
   1. entire vpc
   2. vpc subnet
   3. specific ENI
3. destination options
   1. cloudwatch logs - to perform operations or monitor.
   2. s3 - long term storage for compliance.
   3. aws data firehose - for streaming for analytics. For transforming before storing.
4. collected and do not affect network latency or thruput.
5. supports ELB, RDS, redshift, nat gw.
6. use cases
   1. diagnosing sec grp rules for denied traffic.
   2. monitor traffic.
   3. determine direction of traffic.
7. vpc flow logs field format
   - version, account-id, interface-id, srcaddr, dstaddr, srcport, dstport, protocol, packets, bytes, start, end, action, status
8. use aws athena to query the logs in s3 or cw logs.
9. not for packet inspection.

### VPC traffic mirroring
1. set up a source (ENI to watch), filter, target (destination), session
2. destinations
   1. eni
   2. GwLB
   3. NLB
3. filter and truncate packets.
4. source and targets dont have to be in same acct.
5. use cases
   1. content inspection
   2. threat monitoring

### egress-only internet GW
1. only usable by resources with IPv6 addr.
2. like NAT gw.
3. no charge for use but charged for data transfer.
4. ipv4 and ipv6 are handled by different route tables.
5. you attach egress-only igw to vpc.