# Welcome to the aws-interesting-reads wiki!

## Network:

Some network diagrams: 
Note: 
NAT gateways are always in public subnets.  NGW is better than NAT instance. 
Good practice to have DB &Application logic instances in Private subnets.
Webservers are meant to be accessed over internet. So, place them in public subnet of VPC
 

For IPV6 :
An egress-only Internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows outbound communication over IPv6 from instances in your VPC to the Internet, and prevents the Internet from initiating an IPv6 connection with your instances
 
Bastion Host: 
 
Elastic Network Adapters (ENAs) 
provide traditional IP networking features that are required to support VPC networking. 
Elastic Fabric Adapters 
provide all of the same traditional IP networking features as ENAs, and they also support OS-bypass capabilities. OS-bypass enables HPC and machine learning applications to bypass the operating system kernel and to communicate directly with the EFA device.
VPC Peering :  
No transitive vpc peering. A to B and B to C does not mean A to C is possible.  
Inter region vpc peering is possible which enables communication between multiple vpcs located in different regions.
AWS Transit Gateway:
 is an AWS service that helps customers manage multiple network connections between Amazon Virtual Private Clouds (VPCs) and remote networks.
AWS VPN CloudHub
operates on a simple hub-and-spoke model that the user can use with or without a VPC. This design is suitable for customers with multiple branch offices and existing internet connections who would like to implement a convenient, potentially low-cost hub-and-spoke model for primary or backup connectivity between remote offices. 
VPC End Point:
Interface endpoints
	Gateway endpoints
	Gateway Load Balancer endpoints

An interface endpoint is an elastic network interface with a private IP address from the IP address range of your subnet. It serves as an entry point for traffic destined to a supported AWS service or a VPC endpoint service. Interface endpoints are powered by AWS PrivateLink.
For information about the AWS services that integrate with AWS PrivateLink, see AWS services that integrate with AWS PrivateLink. You can also view all of the available AWS service names..
	Supported services: 
•	Amazon S3
•	DynamoDB
You specify a gateway endpoint as a route table target for traffic that is destined for the supported AWS services.	A Gateway Load Balancer endpoint is an elastic network interface with a private IP address from the IP address range of your subnet. Gateway Load Balancer endpoints are powered by AWS PrivateLink. This type of endpoint serves as an entry point to intercept traffic and route it to a service that you've configured using Gateway Load Balancers, for example, for security inspection. You specify a Gateway Load Balancer endpoint as a target for a route in a route table. Gateway Load Balancer endpoints are supported for endpoint services that are configured for Gateway Load Balancers only.


VPC Endpoints allows DYNMO DB to access securely 

  
## EC2: 

Storage optimized instances are designed for workloads that require high, sequential read and write access to very large data sets on local storage. They are optimized to deliver tens of thousands of low-latency, random I/O operations per second (IOPS) to applications.

Memory Optimized Instances is incorrect because these are designed to deliver fast performance for workloads that process large data sets in memory, which is quite different from handling high read and write capacity on local storage.

Compute Optimized Instances is incorrect because these are ideal for compute-bound applications that benefit from high-performance processors, such as batch processing workloads and media transcoding.

General Purpose Instances is incorrect because these are the most basic type of instances. They provide a balance of compute, memory, and networking resources, and can be used for a variety of workloads. Since you are requiring higher read and write capacity, storage optimized instances should be selected instead

The AWS Nitro System is the underlying platform for the latest generation of EC2 instances that enables AWS to innovate faster, further reduce the cost of the customers, and deliver added benefits like increased security and new instance types.
An Elastic IP address doesn’t incur charges as long as the following conditions are true:
- The Elastic IP address is associated with an Amazon EC2 instance.
- The instance associated with the Elastic IP address is running.
- The instance has only one Elastic IP address attached to it.

If you’ve stopped or terminated an EC2 instance with an associated Elastic IP address and you don’t need that Elastic IP address anymore, consider disassociating or releasing the Elastic IP address.
CloudWatch Logs agent provides an automated way to send log data to CloudWatch Logs from Amazon EC2 instances hence, CloudWatch Logs agent is the correct answer.

The CloudWatch Logs agent is comprised of the following components:
- A plug-in to the AWS CLI that pushes log data to CloudWatch Logs.
- A script (daemon) that initiates the process to push data to CloudWatch Logs.
- A cron job that ensures that the daemon is always running.
Read about 
Compute Savings Plan:  66% discount 
Upto 66% savings.  Works for both EC2 and Fargate.  Lets you change instance’s family and size. 
EC2 Instances Saving Plan :   - 72% discount 
Not applicable to FARGATE instances.
Convertible Reserved Instances:
- Convertible Reserved Instances allows you to exchange for another Convertible Reserved instance with a different instance type and tenancy.

For Amazon Web Services, the reserved instance (standard or convertible) helps the user save money if the user is going to run the same instance for a longer period. Generally if the user uses the instances around 30-40% of the year annually it is recommended to use RI. Here as the instance runs only for 1 hour 50 minutes daily, or less than 8 percent of the year, it is not recommended to have RI as it will be costlier. 

A Lambda layer is a way to include an additional bundle of code dependencies needed to run your lambda function. 

## Elastic BeanStalk: 
  
AWS Elastic Beanstalk can support containers but is not the right choice for batch processing that can create, scale and delete clusters as needed. AWS Elastic Beanstalk is designed to host web applications. 
## Cloud Formation :

## Autoscaling :
Cooldown period:
It ensures that the Auto Scaling group does not launch or terminate additional EC2 instances before the previous scaling activity takes effect.
Its default value is 300 seconds.
It is a configurable setting for your Auto Scaling group.

 
Lifecycle hooks: 
enable an Auto Scaling group to be aware of events in the Auto Scaling instance lifecycle, and then perform a custom action when the corresponding lifecycle event occurs. A lifecycle hook provides a specified amount of time (one hour by default) to complete the lifecycle action before the instance transitions to the next state.

Scaling in decision : 
 






## Storage: 
Amazon S3 

 
S3 is an object storage service that offers industry-leading scalability, data availability, security, and performance. S3 offers different storage tiers for different use cases (frequently accessed data, infrequently accessed data, and rarely accessed data).
S3 Transfer acceleration useful for transferring data to S3 using Amazon cloud front’s globally distributed edge locations thereby increasing data transfer speed. 
1.	Object locks can prevent objects from modification or deletion; objection versioning does not - it only maintains versions of an object until those versions are deleted.
2.	Users can only enable Object locks on new S3 buckets. 
3.	Object locks have two retention modes - governance mode and compliance mode. Compliance mode prevents objects from being deleted or updated by users, including the root user. Governance mode allows objects to be modified, but prevents objects from being deleted.
4.	When using object locking, you first enable the feature at the bucket level, and the system automatically turns on versioning for the S3 bucket.  After turning on bucket-level object locking, there are two ways to manage how the system retains the objects in a bucket: retention periods and legal holds. 
5.	Retention period: Use the retention period to indicate the date that an object lock expires for an individual object.  
6.	Legal hold: (legal cases in question) Use a legal hold on an object to indicate that the object lock does not expire.  With a legal hold, the object lock remains active until a user with the appropriate permissions removes the legal hold.



 
enable the cross-region replication feature in S3, the following items should be met:

The source and destination buckets must have versioning enabled.

The source and destination buckets must be in different AWS Regions.

Amazon S3 must have permissions to replicate objects from that source bucket to the destination bucket on your behalf.

http://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html
https://docs.aws.amazon.com/AmazonS3/latest/dev/ManageCorsUsing.html

more on S3 pricing. See https://aws.amazon.com/s3/faqs/#Billing for some examples such as this one for data requests: Assume you transfer 10,000 files into Amazon S3 and transfer 20,000 files out of Amazon S3 each day during the month of March. Then, you delete 5,000 files on March 31st.
Total PUT requests = 10,000 requests x 31 days = 310,000 requests
Total GET requests = 20,000 requests x 31 days = 620,000 requests
Total DELETE requests = 5,000×1 day = 5,000 requests
Assuming your bucket is in the US East (Northern Virginia) Region, the Request fees are calculated below:
310,000 PUT Requests: 310,000 requests x $0.005/1,000 = $1.55
620,000 GET Requests: 620,000 requests x $0.004/10,000 = $0.25
5,000 DELETE requests = 5,000 requests x $0.00 (no charge) = $0.00

For PCI Compliant : 
Encrypt data in transit.
Monitor access with CloudTrail and VPC Flow Logs.
Use server side encryption to protect card holder data.



S3 Scenarios with SNS and SQS :  
File Encoders
 

## Instance Store
Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers
here are some examples of use cases for EC2 instance storage (ephemeral): https://docs.aws.amazon.com/whitepapers/latest/aws-storage-services-overview/amazon-ec2-instance-storage.html
## EBS 
 

 

EBS snapshots allow you to back up your data stored on EBS volumes and stores them in S3. Each snapshot saves only incremental changes that have occurred since the last snapshot. This approach helps reduce storage costs by not duplicating data with each backup.

When you create an encrypted EBS volume and attach it to a supported instance type, the following types of data are encrypted:

- Data at rest inside the volume

- All data moving between the volume and the instance

- All snapshots created from the volume

- All volumes created from those snapshots

Encryption operations occur on the servers that host EC2 instances, ensuring the security of both data-at-rest and data-in-transit between an instance and its attached EBS storage. You can encrypt both the boot and data volumes of an EC2 instance.

## EFS 

 
Amazon Elastic File System
 is a fully-managed file storage service that makes it easy to set up and scale file storage in the Amazon Cloud.
Amazon FSx For Lustre
 is a high-performance file system for fast processing of workloads. Lustre is a popular open-source parallel file system which stores data across multiple network file servers to maximize performance and reduce bottlenecks.
Amazon FSx for Windows File Server 
is a fully managed Microsoft Windows file system with full support for the SMB protocol, Windows NTFS, Microsoft Active Directory ( AD ) Integration. 
AWS Storage Gateway  
is primarily used to integrate your on-premises network to AWS but not for migrating your applications. AWS Storage Gateway is more suitable if you still want to retain access to the migrated data and for ongoing updates from your on-premises file-based applications.
•	AWS File Gateway: File Gateway is a service you use to extend your on-premises file storage to the AWS cloud without needing to update existing applications that use these files.  With file gateway, you can map on-premises drives to S3 so that users and applications can access these files as they usually would.  Once the files are in S3, you can access them in the cloud from any applications deployed there or continue using these files from on-premises.  File gateway provides access to files in S3 based on SMB or NSF protocols.
•	AWS Volume Gateway:  The Volume Gateway can provide primary storage or backup storage for your on-premises iSCSI block storage devices.  There are two configuration modes when you use volume gateway: cache mode and stored mode.  With cache mode, the system keeps the primary copy of your data in S3, and a local on-premises cache provides low latency access to the most frequently accessed data.  In stored mode, the primary copy of the data is on-premises, and the system periodically saves a backup to S3.  Stored volume gateways create EBS snapshots stored on S3 and are billed as Amazon EBS snapshots.
•	AWS Tape Gateway:  The tape gateway, also known as the Virtual Tape Library, allows you to back up your on-premises data to S3 from your corporate data center.  With tape gateway, you can leverage the Glacier storage classes for data archiving at a lower cost than S3.  The tape gateway is essentially a cloud-based tape backup solution that replaces physical components with virtual ones.


Remember: All 3 storage gateway patterns are backed by S3 not EFS. 
Volume Gateways 
Stored Volume GW vs Cached Vol GW
Stored Volume GW	Cached Vol GW
Primary store is on-prem. Async backs on prem data to S3 	Primary Store S3 
system periodically saves a backup to S3
Stored volume gateways create EBS snapshots stored on S3 and are billed as Amazon EBS snapshots	Retain Copy of frequently accessed on Prem
Low latency access to entire dataset	Low latency access to freq accessed data. 
Useful in disaster recovery 	Cost savings 

Storage GW scenario:
 
AWS Data Sync 
is primarily used to migrate existing data to Amazon S3, EFS and FSx. It is cost effective service when migration is considered. 
While transferring a constantly changing dataset between on-premise servers & EFS using DS, you could initially uncheck Enable verification to avoid verification for delta changes. You can enable verification during the final cut-over from On-prem to AWS. 

AWS DataSync is an online data transfer service that simplifies, automates, and accelerates moving data between on-premises storage systems and AWS Storage services, as well as between AWS Storage services. You can use DataSync to migrate active datasets to AWS, archive data to free up on-premises storage capacity, replicate data to AWS for business continuity, or transfer data to the cloud for analysis and processing.

Both AWS Storage Gateway and AWS DataSync can send data from your on-premises data center to AWS and vice versa. However, AWS Storage Gateway is more suitable to be used in integrating your storage services by replicating your data while AWS DataSync is better for workloads that require you to move or migrate your data.













## All Storage services 


 

## Database :

DMS:
Migrates on-prem db to cloud. On-prem db can be full operational during migration.
Schema Conversion tool –> Heterogenous DB Migration 
Engine Conversion tool –> Homogenous DB Migration 


Dynamo : 
Amazon DynamoDB Accelerator (DAX) 
is a fully managed, highly available, in-memory cache that can reduce Amazon DynamoDB response times from milliseconds to microseconds, even at millions of requests per second.
Amazon DynamoDB
 Can work in tandem AWS Lambda. Useful for storing sessions data. 
Whenever an application creates, updates, or deletes items in the table, DynamoDB Streams writes a stream record with the primary key attribute(s) of the items that were modified. A stream record contains information about a data modification to a single item in a DynamoDB table. You can configure the stream so that the stream records capture additional information, such as the "before" and "after" images of modified items.

## Elastic Cache 

## Aurora: 

An Aurora Serverless DB cluster is a DB cluster that automatically starts up, shuts down, and scales up or down its compute capacity based on your application's needs. Aurora Serverless provides a relatively simple, cost-effective option for infrequent, intermittent, sporadic or unpredictable workloads. It can provide this because it automatically starts up, scales compute capacity to match your application's usage and shuts down when it's not in use.
Take note that a non-Serverless DB cluster for Aurora is called a provisioned DB cluster. Aurora Serverless clusters and provisioned clusters both have the same kind of high-capacity, distributed, and highly available storage volume.
When you work with Amazon Aurora without Aurora Serverless (provisioned DB clusters), you can choose your DB instance class size and create Aurora Replicas to increase read throughput. If your workload changes, you can modify the DB instance class size and change the number of Aurora Replicas. This model works well when the database workload is predictable, because you can adjust capacity manually based on the expected workload.
Aurora Provisioned DB cluster is not suitable for intermittent, sporadic, and unpredictable transactional workloads. This model works well when the database workload is predictable because you can adjust capacity manually based on the expected workload. A better database setup here is to use an Amazon Aurora Serverless cluster
Use case for AAS: Amazon Aurora Serverless  is an on-demand database service that is easy to configure and use. It is well suited for development and test environments, as well as low traffic production workloads. 


## RDS : 
During automated backup, rds creates storage vol snapshot of entire db instance and uploads tx logs to S3 every 5 min. Restoration of DB at specific point in time is possible using DB snapshot. 
READ Multi_AZ :
 https://aws.amazon.com/rds/details/multi-az/
## RDBMS vs Dynamo
 
## REDSHIFT :
https://docs.aws.amazon.com/redshift/latest/mgmt/managing-snapshots-console.html

## Security 
KMS : 
**https://tutorialsdojo.com/aws-key-management-service-aws-kms/**
Client-side encryption
 is the act of encrypting data before sending it to Amazon S3. To enable client-side encryption, you have the following options:
- Use an AWS KMS-managed customer master key.
- Use a client-side master key.

AWS Shield /WAF in AWS App : 
AWS Shield Advanced provides additional detection and mitigation against large and sophisticated DDoS attacks, near real-time visibility into attacks, and integration with AWS WAF, a web application firewall.

 
## AWS Secret Manager :

 

## Serverless : 
LAMBDA and API Gateway are best combination to handle the bursts of traffic in seconds.

READ : https://docs.aws.amazon.com/lambda/latest/dg/invocation-scaling.html

Some serverless example : 
 
Another Serverless example : 
 
## Cloud Watch : 

To monitor custom metrics, you must install the CloudWatch agent on the EC2 instance. After installing the CloudWatch agent, you can now collect system metrics and log files of an EC2 instance.
list of custom metrics that you can set up:
- Memory utilization
- Disk swap utilization
- Disk space utilization
- Page file utilization
- Log collection
## AWS Directory Service : 
Can use existing Microsoft AD or Lightweight Directory Access Protocol (LDAP)–aware applications in the cloud
 
## Amazon API Gateway : 
Amazon API Gateway provides throttling at multiple levels including global and by service call. Throttling limits can be set for standard rates and bursts. For example, API owners can set a rate limit of 1,000 requests per second for a specific method in their REST APIs, and also configure Amazon API Gateway to handle a burst of 2,000 requests per second for a few seconds. Amazon API Gateway tracks the number of requests per second. Any request over the limit will receive a 429 HTTP response. The client SDKs generated by Amazon API Gateway retry calls automatically when met with this response. 
You can add caching to API calls by provisioning an Amazon API Gateway cache and specifying its size in gigabytes. The cache is provisioned for a specific stage of your APIs. This improves performance and reduces the traffic sent to your back end. Cache settings allow you to control the way the cache key is built and the time-to-live (TTL) of the data stored for each method. Amazon API Gateway also exposes management APIs that help you invalidate the cache for each stage.
 
## Load Balancers : 

 
Application LB	Network LB
Choose an Application Load Balancer when you need a flexible feature set for your web applications with HTTP and HTTPS traffic. Operating at the request level, Application Load Balancers provide advanced routing and visibility features targeted at application architectures, including microservices and containers.	Choose a Network Load Balancer when you need ultra-high performance, TLS offloading at scale, centralized certificate deployment, support for UDP, and static IP addresses for your application. Operating at the connection level, Network Load Balancers are capable of handling millions of requests per second securely while maintaining ultra-low latencies.
Application layer	Network layer & Application layer
	Internet & Internal facing
	
	




Associate an Elastic IP address to a Network Load Balancer.

 

## Route 53
Non-Alias with a type "A" record set -> Non-Alias with a type “A” record set for IP addresses.
Alias with a type "CNAME" record set  CNAME record at the zone apex. For example, if you register the DNS name tutorialsdojo.com, the zone apex is tutorialsdojo.com.
Alias with a type of “MX” record set is MX record is primarily used for mail servers. It includes a priority number and a domain name, for examplle: 10 mailserver.tutorialsdojo.com.

## ADFS Integration 
- Setup a Federation proxy or an Identity provider
- Setup an AWS Security Token Service to generate temporary tokens
- Configure an IAM role and an IAM Policy to access the bucket.

 
## SSO Integration :
 


## AWS Config : 
 

## Cloud Front : 
Cloud Front  - is a global service .. Content Delivery Network. 
Edge location where content is cached.
Distribution – Collection of EDGE locations. 
Web Distribution  ->  html css etc  over HTTP/HTTPS
RTMP Distribution  -> media files from S3 bucket. Supports Live streaming etc. Signed cookies aren't supported for RTMP distributions 
TTL  : Invalidating the cache is chargeable
RTMP distribution..
Use signed cookies for the following cases:
- You want to provide access to multiple restricted files, for example, all of the files for a video in HLS format or all of the files in the subscribers' area of a website.
- You don't want to change your current URLs
- Eg . Amazon prime subscription 

Use signed URLs for the following cases:
- You want to use an RTMP distribution. Signed cookies aren't supported for RTMP distributions.
- Signed URLs are primarily used for providing access to individual files
Use Cloud front origin to restrict bucket access through OAI.  
Configure your S3 bucket to remove public read access and use pre-signed URLs with expiry dates
 
The Cache-Control and Expires headers control how long objects stay in the cache. The Cache-Control max-age directive lets you specify how long (in seconds) you want an object to remain in the cache before CloudFront gets the object again from the origin server. The minimum expiration time CloudFront supports is 0 seconds for web distributions and 3600 seconds for RTMP distributions.
For PCI or HIPAA compliant :  
Enable cloud front access logs. 
Capture request that are sent to the Cloud Front API. 




 
## Cloud Formation: 
CloudFormation, a template is a JSON or a YAML-formatted text file that describes your AWS infrastructure. Templates include several major sections. The Resources section is the only required section. Some sections in a template can be in any order. However, as you build your template, it might be helpful to use the logical ordering of the following list, as values in one section might refer to values from a previous section. Take note that all of the sections here are optional, except for Resources, which is the only one required.

- Format Version

- Description

- Metadata

- Parameters

- Mappings

- Conditions

- Transform

- Resources (required)

- Outputs

## SQS
Quick facts about SQS Long Polling:

- Long polling helps reduce your cost of using Amazon SQS by reducing the number of empty responses when there are no messages available to return in reply to a ReceiveMessage request sent to an Amazon SQS queue and eliminating false empty responses when messages are available in the queue but aren't included in the response.

- Long polling reduces the number of empty responses by allowing Amazon SQS to wait until a message is available in the queue before sending a response. Unless the connection times out, the response to the ReceiveMessage request contains at least one of the available messages, up to the maximum number of messages specified in the ReceiveMessage action.

- Long polling eliminates false empty responses by querying all (rather than a limited number) of the servers. Long polling returns messages as soon any message becomes available.

## AWS Cert Manager
AWS Certificate Manager (ACM) handles the complexity of creating, storing, and renewing public and private SSL/TLS X.509 certificates and keys that protect your AWS websites and applications. You can provide certificates for your integrated AWS services either by issuing them directly with ACM or by importing third-party certificates into the ACM management system. In addition to requesting SSL/TLS certificates provided by AWS Certificate Manager (ACM), you can import certificates that you obtained outside of AWS. You might do this because you already obtained a certificate from a third-party issuer, or because the certificates provided by ACM do not meet your requirements. After you import a certificate, you can use it with the AWS services that are integrated with ACM. The certificates that you import work the same as those provided by ACM, with one important exception: ACM does not provide managed renewal for imported certificates, meaning that you will need to remember when the certificate expires and renew it using your own means.
IAM certificates should be used only when you must support an SSL connection in an AWS Region that does not support AWS Certificate Manager (ACM) certificates.


## Data transfer Cost: 
The data transferred between Amazon EC2, Amazon RDS, Amazon Redshift, Amazon ElastiCache instances, and Elastic Network Interfaces in the same Availability Zone is free. Instead of using the public network to transfer the data, you can use the private network to reduce the overall data transfer costs


 ## For Reads: 

https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html

https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/replacing-lost-key-pair.html

https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-choosing-alias-non-alias.html  -- must read

https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-overview.html



Making bastion host HA using NLB (since communication is at OSI layer4)
Gamers around the world need low latency - uses UDP protocol and scalable DB -> use NLB and DynamoDB. UDP works at layer4, so use NLB.
RDS with multi-AZ vs read replicas. Synchronous vs asynchronous replication in RDS. Reads are async.
Creating reader/writer endpoint on a Aurora replica - concept of custom endpoint was clearly explained on a TD exam question
Aurora serverless with on-demand capacity vs Aurora with provisioned capacity
Changing schemas - use Dynamo DB
Streaming data - use Kinesis data streams. Distractor was Kinesis FH writing to DynamoDB. Note: Kinesis FH can only load data to: S3, Elasticache, Redshift and Splunk.
Amazon Kinesis Data Firehose only supports Amazon S3, Amazon Redshift, Amazon Elasticsearch, and an HTTP endpoint as the destination.
S3 event notification to trigger a Lambda. Note: S3 event notification can trigger only SNS, SQS and Lambda.
Using CF with Lambda@edge to perform dynamic computations and reduce traffic between CF and S3 origin thereby reducing network cost
Snowball edge (for computing on the way to AWS location)
S3 transfer acceleration vs multipart upload
S3 cross region replication: Massive S3 in a US region1. You create S3 in a second US region2. You need to copy from region 1 to 2 one time. One option could be Snowball (or Snowmobile) since its the same country. But, due to a specific restriction, Snowballs aren't allowed. So, best option was enabling cross region replication.
If RDS wasn't encrypted at creation, create snapshots and encrypt with copy, load DB into copied version, destroy old version - this was clearly explained on one TD question
R53 for HA - use failover routing. Weighted records can help in distributing loads across EC2s fronted by an ALB.
Global accelerator vs cloudfront. There could be a distractor saying you need to enable caching in CF. The whole concept of using CF is to have caching at edge - so ignore that. If question is about increasing TTL on CF, then that's a valid option based on the scenario.
AWS well architected security concept: refer SG in another SG instead of referring to VPC CIDR blocks or ASG CIDR blocks - this was clear on a TD exam question
KMS vs secrets vs SSM vs HSM - this was very confusing
S3 encryption at rest where customer manages keys and encryption. Don't use SSE-C, use client side encryption.
SCPs and OUs
IAM related questions - I must have failed all of those!
ASG lifecycle hook: termination wait concept - to save EC2 data during a scale-in - this was clear on a TD exam question and also on Stephane's course
2 questions on S3 IT (intelligent tiering) - you are unsure of S3 usage patterns and so choose IT
Storage gateways - file vs volume. There was a very confusing question on this one. I thought I knew the difference between the 3 SGs very well but the way question was framed totally confused me, must have got it wrong.
WAF only on ALB, API G and CF - remember WAF doesn't work on CLB (its a distractor). WAF using rate based rules to help with DDOS, Shield doesn't have such a feature (advanced is just access to the DRS team and waiver of the annual fee if DDOS happened). WAF also takes care of XSS.
Transit Gateway to manage multiple VPCs and other components
HA for NAT instances: replace by NAT Gateways in multi AZ (diffent public subnets).
To reduce cost, remove a NAT gateway and replace all intra VPC communication by creating an endpoint. Note: NAT gateway costs money.
SNS + SQS fan-out - multiple consuming services, default SQS retention is 4 days (can be increased to 14)
Concept of decoupling using SQS. Some really confusing options there. I may have hit the wrong option there. Never got such a confusing SQS one on any test!
Scheduled reserved instances (remember this is for 1 year)
One question on AWS batch, looks like this was a distractor but can't say. I may have got it incorrect.
Step functions (orchestration of multiple steps). Confusing question there. It looked like orchestration is desired but not required. I must have got this one wrong.
Reading some JSON S3 bucket/object policies (PUT, DELETE, UPDATE, LIST operations).
Enabling SG and NACL to allow internet connectivity to an EC2 instance (which is launched with default settings). Note: SG is stateful, so only open in-bound. NACL is stateless - open both inbound and outbound. Otherwise, internet access will be one way (only inbound) and no response back from the EC2s.
S3 pre-signed URLs for premium users. Short lived pre-authenticated URLs.
EC2 detailed monitoring, cloudwatch metrics, event logs. I must have got all of these wrong!
Can you put on-prem data directly in S3 deep archive using file gateway? Can you? I don't know and I am in no rush to find out right away :)
Lots of questions with themes around hybrid cloud - company has on-prem users and data and wants to migrate to AWS but maintain the on-prem. AWS is pushing/encouraging all big corps to go to hybrid cloud because companies cannot throw away their existing infrastructure. This concept was well explained by Stephane.
If data retrieval allowed is a week, then cheapest option to store is Glacier deep archive instead of other S3 classes. Note: standard and bulk retrieval options need 12 and 48 hours respectively on deep archive. For glacier, it takes up to 5 mins on expedited mode (recommended to use provisioned capacity), up to 5 hours for standard retrieval and up to 12 hours for bulk.
Cost explorer vs AWS budgets
One question on Redshift (BI analytics related) but it was confusing. Though it seemed the question was about reporting, it also sounded like a normal OLTP. It didn't say OLAP. Is Redshift cluster costlier than provisioned RDS? If so, I may have got this one wrong.
EFS is Posix based. If on-prem has all windows file servers, then use FSx for windows while migrating
For extremely low latencies between EC2s, use cluster placement group
Simple question on elasticache
user sessions can be saved on elasticache and dynamoDB
One question on auditing using Cloudtrail
Some confusing questions on IAM policy vs resource policy - I have been horrible with getting a grip on IAM and didn't spend much time preparing this part. Must have got these wrong!
But, I think its important to remember some key points which TD makes it succinctly clear: IAM can be enabled on RDS PostgreSQL and MySQL and also on Aurora (MySQL or PostgreSQL) but not on MSSQLserver or Oracle or MariaDB (TDE encrytion available on MSSQL and Oracle for DB in place encryption). Redis doesn't support direct IAM integration - have to use RedisAuth; use cases of IO1, GP2, ST1 and SC1; minimum retention period in every S3 storage tier; application has to delete the SQS processed messages or duplicates will arrive (unless queue expiry is reached-default is 4 days); how to use OAI on CF for S3 as an origin.
No questions on:
ECS cluster, EKS, Fargate, cloud formation, beanstalk, opsworks, code deploy/build/commit, Glue, Neptune, S3 byte-range fetch; parallelizing S3 reads/multi-part upload, S3/Glacier select,  surprisingly nothing on Athena as well, Cognito, SAM, Elasticsearch
TD has some questions on blue-green deployment (I think more relevant on AWS developer associate), MySQL DB engine InnoDB, DNSSEC record type not currently supported by R53, Lamdba canary and other deployment options (when deploying newer versions) - I think these aren't ones one should focus much on but then AWS has a massive question pool and Jon and team have meticulously developed these. So, who knows you might be better off understanding these.
On a personal front, I had the good fortune of going to a free AWS sponsored event (pre pandemic) in an AWS office where we migrated a SQL server to RDS. We did the whole simulation and AWS experts helped us do this. At that time, I had not much idea about real differences between DB on an EC2 vs on provisioned RDS! At work, we have a huge mandate to migrate an IBM machine on-prem to cloud- hybrid and full public cloud plus there are a host of other applications to either create from scratch on AWS or move to public cloud. Cloud technologies are going to rule the future and the three big ones will continue to dominate: AWS, Azure and GCP.
