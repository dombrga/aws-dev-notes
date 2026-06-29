## June 23, 2026

### aws direct connect
1. cloud svc to establish dedicated conn from your premises to aws.
2. private conn between your data center and aws.
3. can reduce network cost, increase bandwidth throughput.
4. set up between data center and aws.
5. needs VGW.
6. DX connection types
   1. dedicated
      -  associated with single customer
   2. hosted
7. direct connect is not immediately available to use.
8. traffic in direct connect is private but not encrypted. Need to overlay VPN to encrypt, but requires more overhead.

### direct connect gateways
1. globally available.
2. allows to connect to multiple vpcs using single direct conn.
3. centralized point for managing conn between onprem and aws resources.

### aws transit gateway (TGW)
1. connects VPCs and onprem networks through a central hub. VPC and VPNs are attached to TGW and routes traffic between them.
2. simplifies network.
3. EXAM TIP: TGW supports IP multicast.
4. common TGW attachments
   1. vpc attachments
   2. vpn attachments
   3. peering attachments.
5. tgw route table config use cases
   1. network segmentation
   2. hub and spoke
   3. shared services
   4. complex routing scenarios.