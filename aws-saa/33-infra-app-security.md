# aws certificate manager (acm)
1. svc to create, manage and deploy public and private tls cert.
2. offers private CA option.
3. commonly integrates with
   1. ELB
   2. cf distributions
   3. amazon api gw - regional and edge-optimzed gw
4. cannot directly associate with ec2 instances.

### public tls certs
1. request and use public tls cert for free.
2. still pay for resources using them.
3. auto renewal of acm-issued tls cert. Auto renew 60 day s before expiration if still valid.

### types of domain to know
1. FQDN - complete address of a host on the internet to specify exact location. Example, **www.pluralsight.com**.
2. wildcard domain - to match all possible subdomains with one cert. Like **blog.pluralsight.com** and **app.pluralsight.com**.

### methods of validating domain ownership
1. dns validation
   - recomm method and requred for auto renewal to work
   - create CNAME
2. email validation
   - not recomm

### importing tls certs
1. can import cert from godaddy, digicert, etc.
2. no auto renewal.
3. To renew, need to get new cert and import again.

### regional and global cert req
1. regional resources require acm certs in the same region.
2. global resources need acm in us-east-1.
   - edge-optimized gw and cf need an acm cert in us-east-1.