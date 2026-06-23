## June 19, 2026

### Route 53
1. DNS. Convert URLs to IP addr.
   - top-level domain name is the .com.
   - second level domain name is netflix in **netflix**.com.
   - www is subdomain.
2. route53 DNS service of aws.
   - highly available.
   - SLA of 100%.
   - port 53.
   - domain registrations, dns routing, health checks.
3. authoritative. You control all updtes of dns records.
4. domain registar assigns domain names under 1 or more TLD.
5. domain registration, dns routing config, and health checks.

### Hosted zones
1. containners for records to specify how to route traffic to domains or subdomains.
2. 2 types
   1. public hosted zone
      - conatins records for for public internet.
   2. private hosted zone
      - for private domain names.
      - used with VPCs.
3. not free.

## June 23, 2026

### DNS record
1. dictates how and wherey you want dns traffic routed.
2. record
   - domain: pluralsight.com
   - record type: A, CNAME, MX, NS, SOA.
     1. A - IPv4
     2. AAAA - IPv6
     3. NS - name servers
     4. CNAME - maps one dns name to another domain. Like www.asd.com ---> www.qwe.com
   - value: what resource do you want to route traffic to?
     - you can put multiple ipaddr here.
   - routing policy: how to respond to dns query.
   - ttl: how long dns resolvers cache a record value.
3. in exam, you should likely choose alias record over CNAME.

### Routing policy
1. setting for records to determine how route53 responds to dns queries.
2. simple routing policy
   - for single resources and ip addr.
   - alias recrods points to a single AWS resource, like ELB.
   - supports multiple values for same record.
   - returns values in random order.
3. weighted routing policy
   - set for multiple resources under single domain or subdomain.
   - control % of traffic thats routed to each resource.
   - use records with same name and type.
   - set weight to 0 to stop traffic to that resource.
4. failover routing policy
   - active-passing routing
   - routes traffic to a healthy resource but once marked unhealthy, it responds with healthy secondary resource.
   - secondary on standby.
5. multivalue answer routing policy
   - returns multiple values for dns queries.
6. geolocation routing policy
   - choose where traffic is sent based on geographic location of user/requester.
   - for localization of restricting access to content based on loc.
   - example: you want all european queries to go to web server hostedo n eu-west-2.
   - should have default record in place in case there is no match.
   - not based on latency.
6. latency-based routing policy
   - route traffic to lowest network latency, even if it is in another aws region.
7. geoproximity policy
   - you can specify a value of **bias** to route more or less traffic to a resource
8. can use Traffic flow for complex policies

### route53 health checks
1. on individualrecords.
2. if record fails health check, will be removed from route53 until is it healthy..
3. types
   1. monitoring an endpoint
      - rout5e54 uses ~15 global health checkers.
      - interval can be 30 or 10 secs.
      - results in 2xx or 3xx dode.
      - ensure firewall allows health checkers.
      - for publicly resolvable records.
   2. monitoring other health checks
      - aka calculated health checks.
      - combining multiple HC into one.
   3. monitoring cloudwatch alarms
      - perfect within private hosted zones.

### route53 resolvers.
1. hybrid DNS. Mixed of onprem and cloud-based sources.
2. manage dns records for onprem and aws resources.
3. route53 resolver. DNS resolver that responds recursively to dns queries from aws resources.
4. resolver endpoints and rules.
   1. inbound endpoints
      - resolved dns queries coming into vpc.
   2. outbound endpoints
      - going out of vpc.
5. route54 resolver dns firewall.
   - allows or deny access outbound dns traffic.
   - blocks dns-level threats.
   - you can specify lists of domain names to allow or block.
   - can customize response to dns queries.

### advanced VPC: VPN
1. to establish encrypted connection between devices over public internet.
2. 4 primary vpn methods to connect to aws vpc.
   1. site-to-site (s2s).
      - must use publicly resolvable ip addr on your side of vpn conn.
      - most secure.
      - must enable route propagation.
      - IPSec VPN.
   2. aws client vpn
      - managed client-based vpn.
      - aws managed version of openvpn
      - allows you to connect to your resources from anywhere in the world.
      - uses TLS.
   3. aws vpn cloudhub
      -  to securely communicate from site to another s2s vpn.
      -  hub and spoke vpn model.
      -  can be used without vpc in place.
      -  perfect for multiple data centers.
      -  to simply S2S vpn conn management.
   4. 3rd party vpn
      -  obtained from aws marketplace.
      -  use cases; need transitive routing, features no in aws-managed vpn, bandwidth considerations.
      -  need to disable source/destination check on ec2 instance, failover is your responsibility. Plan EC2 sizing.
      -  not recommended for exam scenarios.
1. virtual private gateway (VGW) is a vpn concentrator.
   - deployed on aws side.
   - create a vgw and attach to vpc to create s2s vpn conn.
   - can customize autonomous number system (ASN).
2. customer gateway (cgw)
   - software appliance or physical networking device on the customer side of vpn conn.
   - represents all the info relevant for the vpn conn.
3. use cases
   1. securing hybrid cloud archi.
   2. implementing disaster recovery.
   3. interconnecting vpcs.
   4. establishing transit vpcs.
   5. to connect to 3rd party vendors