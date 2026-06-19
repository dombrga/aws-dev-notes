# AWS IAM, VPC, EC2, EBS,Networking, Compute, S3 Notes

---

## May 25, 2026 — VPC Basics

1. Default VPC is auto-created.
2. Components: CIDR block, subnets, route tables, security groups, NACLs, network gateway.
3. AWS VPC is a **regional** resource, not global.
4. Soft limit of **5 VPCs per region**.
5. Private IP address spaces — not publicly resolved.
6. Includes: DHCP options, main route table, main NACL.

---

### VPC Internet Gateway

1. Allows communication between VPC and the internet.
2. Supports IPv4 and IPv6.
3. Created separately from VPC.
4. Attachable to a **single VPC**.

---

### VPC Subnet

1. Range of IP addresses within a VPC for hosting.
2. Bound to a single AZ and a single route table.
3. Supports IPv4, IPv6, or dual stack.
4. Types: public, private, VPN-only, isolated.
5. **Reserved addresses** (5 total): network address, VPC router, VPC DNS server, future use, broadcast address.
6. VPC does **not** support broadcast traffic.
7. **Public subnet** — has a direct route to the internet via IGW.
8. **Private subnet** — no direct route to internet; requires NAT to access the internet.
9. **Multi-tier architecture in VPC:**
   - **Web frontend tier** — public-facing.
   - **App/backend tier** — not accessible outside VPC; called by web tier.
   - **Database tier** — accessible only within VPC; called by backend tier.
10. Subnets can communicate cross-AZ or cross-region.

---

## May 26, 2026 — Route Tables, NACLs, Security Groups, DHCP

### VPC Route Table

1. Two types:
   - **Main route table** — comes with VPC; default table for unassociated subnets.
   - **Custom route table** — you define and associate with subnets.
     - Fields: Destination, Target, Local Route, Association. Destination is reached through the target.
2. Best practice: 1:1 relationship between subnets and route tables.

---

### Network ACLs (NACLs)

1. **Stateless** — work at the subnet level.
2. Allow/deny inbound and outbound traffic.
3. One NACL per subnet; default NACL is provided.
4. New NACLs **deny all traffic by default**.
5. Do not filter: AWS DNS, DHCP, EC2 instance metadata, reserved IP addresses.
6. **Ephemeral ports** — short-lived ports used when sending responses back to clients.

---

### Security Groups

1. Controls what traffic is allowed to reach or leave a resource.
2. Applied at the resource level (e.g., EC2) and network interface level.
3. Attached to a single VPC.
4. **Only defined allow rules** — no explicit deny.
5. Components:
   - Protocol allowed
   - Port range allowed
   - Target or destination allowed

---

### DHCP

1. Set of network settings associated with a VPC.
2. AWS region has a default DHCP option set.
3. **Cannot modify DHCP** once created.

> AWS reserves **5 IP addresses** per subnet.

---

### VPC Peering

1. Enables secure, direct communication between VPCs.
2. Traffic remains within the AWS network.
3. Supports cross-account, same-account, and cross-region.
4. Peered VPCs **cannot have overlapping IP CIDRs**.
5. Does **not** allow transitive routing.

---

### NAT Gateway

1. Connects private networks to public networks (e.g., internet).
2. Instances in private subnets can connect outside the VPC.
3. Must be deployed in a **public subnet** with direct IGW access.
4. NAT **cannot receive** inbound connection requests.
5. Prefer **NAT Gateway** over NAT Instance.
6. Auto-scales as needed.
7. Deployed to a single AZ; uses an Elastic IP address.
8. For true resiliency, deploy NAT in **multiple AZs**.
9. You do **not** assign a Security Group to a NAT Gateway.

---

### Elastic IP Address

1. Static IPv4 address.
2. Allocated to an AWS account — regional and does not change over time.

---

## May 27, 2026 — Transit VPC, PrivateLink, Endpoints

### Transit VPC

- Attach a VGW (Virtual Gateway) to a VPC.

---

### AWS PrivateLink (APL)

1. AWS services leverage public endpoints by default.
2. PrivateLink allows private resources to communicate with services entirely within the AWS private network.
3. No need for IGW, NAT Gateway, VPN, or Direct Connect.
4. Powers **VPC Interface Endpoints**.

---

### Gateway Endpoint

1. For privately accessing **S3** and **DynamoDB** from a VPC without traversing the public internet.
2. No security group updates required.
3. **Free**.

---

### VPC Interface Endpoints

1. Deploys an ENI to a VPC subnet.
2. Requires a security group.
3. Supports more services than Gateway Endpoints.
4. **Not free**.

---

## EC2

1. IaaS computing service — a virtual machine.
2. Resources: vCPU, RAM, bandwidth, storage (virtual HDD, temporary, cache, network storage).
3. **Key pair** — credentials used when connecting to EC2; public and private key (you download the private key).
4. **AMI** — image used to launch an instance; can be public or private. Artifacts can be embedded in an AMI.

---

### EC2 Sizes and Instance Types

- Defined by **class** and **generation**.

---

### EC2 Hibernate

- Signals the OS to perform hibernation (saves RAM state to disk).

---

## May 28, 2026 — EC2 Storage

### EBS (Elastic Block Store)

1. Volume attached at EC2 creation is the **root data volume**.
2. Network-attached but behaves like a normal HDD/SSD.
3. Standard EBS volumes are bound to a **single EC2 instance** and a **single AZ**.
4. Key attributes: capacity, price.
5. Root volumes are **deleted** when EC2 is terminated; additional volumes are not.
6. Can be replicated within a single AZ; can add capacity without downtime.
7. Can encrypt root and additional volumes.
8. **Cannot directly encrypt** an already-created EBS volume.

#### EBS Volume Types

1. **General purpose** (gp2/gp3)
2. **Provisioned IOPS SSD** — for high I/O demands
3. **Magnetic** — for data archiving and backup

#### EBS Snapshots

1. Point-in-time copy of an EBS volume for backup.
2. Can be shared between AWS accounts and regions.
3. Stored in S3 (no direct access to that S3 storage).

---

### EC2 Instance Store

1. Temporary storage — suitable for buffers, caches, scratch data.
2. Size depends on EC2 device type/size.
3. Data **survives reboots** but is lost on stop, hibernate, or termination.
4. Do **not** store critical data here.

---

### Connecting to EC2

1. Methods: SSH, RDP, EC2 Instance Connect, Session Manager.
2. Prefer **Systems Manager Session Manager** over a bastion host.
3. Session Manager uses the **SSM Agent** (not SSH/RDP); provides centralized access via IAM. Requires IAM permissions and network connectivity.

---

### IMDSv2

- Instance metadata service; accessible at `169.254.169.254`.

---

### ENI (Elastic Network Interface)

1. Networking component that is part of a VPC.
2. Created and bound to a single AZ.
3. Can be attached, detached, and reattached to any EC2 in the same AZ.
4. Supports IPv4/IPv6, security groups, and ephemeral IPv4.

---

### EIP (Elastic IP Address)

- Static IPv4 address scoped to a specific region.

---

## June 8, 2026 — Advanced EC2 Networking & Pricing

### AWS Outpost

- Extends AWS services to on-premises environments (physical rack and server offering).

---

### EC2 Network Types

1. **ENI** — basic networking
2. **EN (Enhanced Networking)** — single-root I/O for high performance
3. **EFA (Elastic Fabric Adapter)** — accelerated HPC/ML networking
4. Enhanced Networking options:
   - **Elastic Network Adapter** — up to 100 Gbps
   - **Intel 82599** — up to 10 Gbps (older instances)
5. **EFA** — for HPC/ML networking; Linux only.

---

### Placement Groups

| Type | Use Case |
|---|---|
| **Cluster** | Single AZ, low latency |
| **Spread** | Critical EC2 instances and apps |
| **Partition** | HDFS, HBase, Cassandra |

---

### EC2 Pricing

1. **On-Demand** — pay by the hour or second.
2. **Reserved Instance** — discounted; being phased out.
3. **Capacity Reservation** — reserve compute for any duration; charged even when not in use.
4. **Savings Plans:**
   - *Compute Savings Plans* — most flexible; covers EC2, Fargate, Lambda; ~66% off on-demand.
   - *EC2 Instance Savings Plans* — committed to a specific instance family in a region; only EC2; ~72% off; can change size, OS, tenancy.
   - *SageMaker Savings Plans*
5. Commitment terms: **1 year** or **3 years**.

---

### Dedicated Options

| Option | Description |
|---|---|
| **Dedicated Host** | Physical server for you; strong compliance; BYOL; full hardware visibility. |
| **Dedicated Instance** | EC2 on hardware dedicated to a single AWS account; partial BYOL. |

---

### Spot Instance

1. Uses spare EC2 capacity at lower cost than on-demand.
2. Do **not** run critical workloads on Spot instances.

---

### EFS (Elastic File System)

1. Managed NFS — can be mounted by **many EC2 instances** simultaneously.
2. Multi-AZ, highly available, and scalable.
3. More expensive than EBS.
4. Use VPC security groups to control access.
5. Good for CMS and simple web servers.
6. Scales to thousands of concurrent NFS client connections and petabyte sizes at up to 20 Gbps throughput.

#### Performance Modes

| Mode | Notes |
|---|---|
| **General Purpose** | Default; web servers, CMS. |
| **Max I/O** | Previous gen; higher per-operation latency. |

#### Throughput Modes

| Mode | Notes |
|---|---|
| **Elastic** | Default; for spiky/unpredictable workloads. |
| **Provisioned** | When performance requirements are known. |
| **Bursting** | Throughput scales with amount of storage in EFS. |

#### Storage Classes

| Class | Notes |
|---|---|
| **Standard** | High-speed SSD; most expensive. |
| **Infrequent Access (IA)** | Lower cost; for audit/historical analysis. |
| **Archive** | Cost-optimized; accessed a few times/year; ~50% cheaper than IA. |

#### File System Types

- **Regional** — across multiple AZs.
- **One Zone** — within a single AZ.

> Use **lifecycle policies** to automatically move data between storage classes.

---

## June 9, 2026 — FSx & S3

### FSx for OpenZFS

- Supports open-source OpenZFS file system.
- Compatible with macOS, Windows, Linux.
- Uses NFS protocol.
- Backups stored in S3.

---

### S3

1. Object storage — any file type.
2. Low cost, highly scalable; unlimited data and objects.
3. Maximum object size: **5 TB**.
4. Not suitable for use as an OS or database.
5. Use cases: backups, archiving, media hosting, static websites.
6. **Buckets** — containers for objects; name is globally unique; buckets are regional.
7. S3 Standard stores across **≥3 AZs** in a region.
8. **Read-after-write consistency** and **strong consistency**.
9. Returns **HTTP 200** on successful upload.

#### S3 Objects

1. Object has a **key** (name) and **value** (data).
2. Can have prefixes; object key is the full path.
3. Objects can have multiple **versions** and **metadata**.
4. **Multipart Upload** — uploads in parts; recommended for objects >5 GB.
5. **Tagging and metadata** — extra data (e.g., Content-Type, Last-Modified).

---

### S3 Storage Classes

| Class | Notes |
|---|---|
| **S3 Standard** | Default; most use cases. |
| **Express One Zone** | High performance. |
| **S3 Standard-IA** | Infrequent access; multi-AZ. |
| **S3 One Zone-IA** | Less resilient; ~20% cheaper. |
| **Glacier Instant Retrieval** | Rarely accessed; immediate retrieval. |
| **Glacier Flexible Retrieval** | Not for real-time access. |
| **Glacier Deep Archive** | Up to 48-hour retrieval. |
| **Intelligent-Tiering** | Automatically moves data between tiers. |

---

### S3 Versioning

1. **Unversioned** by default.
2. Versioning is at the bucket level; cannot turn off — only **suspend**.
3. Writes and deletes create new versions.
4. Good protection against accidental deletion.
5. Deletions add a **delete marker** (object is hidden, not removed).

---

### S3 Lifecycle

1. Manages lifecycle of objects in a bucket.
2. Example: transition from S3 Standard → S3 IA after a set number of days.

---

### S3 Replication

1. Replicates objects from one bucket to another (not immediate/synchronous).
2. **Versioning must be enabled** on both source and destination buckets.
3. Existing objects are **not** replicated — only subsequent objects.
4. Supports cross-region and same-region replication.
5. Buckets do not need to be in the same account.
6. IAM permissions required.

---

## June 10, 2026 — S3 Advanced Features

### S3 Batch Operations

1. Perform a single operation on many objects at once.
2. Example: copy large amounts of data between S3 buckets.
3. Runs via **jobs**; tracks progress, handles retries, sends notifications.

---

### S3 Select

1. Filters object contents using **SQL** on the S3 side.
2. Reduces the amount of data transferred.
3. Best for **small-scale queries**.

---

### S3 Storage Lens

1. Analytics on object storage and activity.
2. Provides metrics and insights.
3. Export to CSV or other formats.
4. Used to find and report data anomalies.
5. Available in **free** and **advanced** tiers.

---

### S3 Event Notifications

1. Receive notifications when S3 events occur.
2. **Not real-time**.
3. Event destinations:
   - **SNS Topic** — push-based
   - **SQS Queue**
   - **Lambda Function**
   - **EventBridge Bus** — for complex filtering and forwarding

---

### S3 Transfer Acceleration

1. Speeds up data uploads and downloads using **edge locations**.
2. Use case: uploading to a central bucket from users spread globally.

---

### S3 Requester Pays

1. The caller pays instead of the bucket owner.
2. Authenticated via AWS IAM.
3. Header: `x-amz-request-payer`

---

### S3 Static Web Hosting

1. S3 can host static websites.
2. Client-side scripts are supported; no server-side processing.
3. No dynamic websites or database connections.
4. Requires **public read access**.

---

## June 12, 2026 — S3 Performance

1. **3,500 req/sec/prefix** for PUT, POST, DELETE.
2. **5,500 req/sec/prefix** for GET.
3. Spread requests across different prefixes to increase throughput.
4. Use **byte-range** fetches for parallel downloads.

---

## June 16, 2026 — S3 Security

### S3 Security Overview

1. Supports **identity-based** and **resource-based** policies.
2. **S3 Bucket Policy** is resource-based; use cases:
   - Allow public access
   - Require encryption
   - Allow cross-account access
3. S3 buckets and objects are **private by default**.
4. **Block Public Access** setting available at bucket/account level.
5. `"Principal": "*"` — grants access to everyone.
   - `bucketname` → bucket-level
   - `bucketname/*` → object-level

---

### S3 ACLs

1. Bucket ACL and object ACL available.
2. Bucket policies are preferred.
3. AWS recommends **turning off ACLs**.

---

### S3 Encryption at Rest

1. **Enabled by default**.
2. Encryption options:
   - **SSE-S3** — managed by AWS; default.
   - **SSE-KMS** — AWS KMS-managed keys; more customizable; requires additional permissions and incurs extra charges; useful for compliance requirements.
   - **SSE-C** — customer-managed keys; you fully manage and use your own keys; S3 has no access to the key.
   - **Client-side encryption** — encrypted before upload.
3. Header: `x-amz-server-side-encryption` = `AES256` or `aws:kms`