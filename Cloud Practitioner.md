# Module 1

## Introduction

AWS offers services ranging from basic elements like compute, storage, and network security to complex solutions like BC, AI, ML

Modern computing centers around a client-server mode. In AWS, the server is represented by an Amazon Elastic Compute Cloud (EC2) instance, which is like a virtual server.

One key concept of AWS is that you only pay for what you use, contrasting with traditional on-premises data centers where capacity is fixed, so you can scale up or down with a click.

## Cloud Computing

Cloud computing is the **on-demand delivery** of **IT resources**** over the internet **with** pay-as-you-go pricing**, so it's more than just computing without on-premise (also called

private cloud deployment) data centers.

**On-demand delivery** means you can get resources like virtual servers and storage when you need them without advance notice so you can easily scale up or down as your needs change, unlike managing your own data centers.

AWS aims to handle common and time-consuming tasks, allowing you to focus on unique aspects of your business.

Resources are accessible **over the internet** , either through a secure webpage console or programmatically

Pay-as-you-go pricing means you only pay for the resources you use.

### Benefits of cloud computing:

**Trade upfront expense for variable expense** : Cloud computing allows companies to move from investing heavily in upfront expenses like data centers and physical servers to paying only for the computing resources they actually use, reducing costs and enabling innovative solutions.

**Stop spending money to run and maintain data centers** : Cloud computing lets companies focus less on managing infrastructure and servers and more on applications and customers, saving both money and time.

**Stop guessing capacity** : With cloud computing, there's no need to predict infrastructure capacity in advance. Resources can be launched when needed, scaling up or down as demand changes, eliminating the need to pay for unused resources.

**Benefit from massive economies of scale** : Cloud providers like AWS can offer lower costs due to economies of scale resulting from aggregating usage from many customers, resulting in lower pay-as-you-go prices.

**Increase speed and agility** : Cloud computing's flexibility allows for faster development and deployment of applications, providing more time for experimentation and innovation compared to traditional data center computing.

**Go global in minutes** : The AWS Cloud's global footprint allows for quick deployment of applications to customers worldwide with low latency, ensuring access with minimal delays, regardless of geographical location.

# Module 2: Compute in the Cloud

## Introduction

Amazon Elastic Compute Cloud (Amazon EC2), basically a VM (configured using an Amazon Machine Image (AMI)), provides **secure** , **resizable** compute capacity in the cloud following the Compute as a Service (CaaS) model.

**Ease of Getting Started with EC2** : AWS has already built, secured, and deployed servers in data centers, making it easy for users to get started with EC2. Users can request EC2 instances, which launch within minutes, and terminate them when they are no longer needed, eliminating the commitment to unused servers. Each EC2 instance has its own storage called an EC2 instance store.

**Cost Flexibility** : Users only pay for running EC2 instances, not for stopped or terminated ones, providing cost flexibility.

**Multitenancy and Hypervisor** : EC2 instances share physical host machines with other instances (virtual machines) using virtualization technology. A hypervisor manages the sharing of physical resources while ensuring **security** and **isolation** among instances.

**Configuration Control** : Users have control over the configuration of EC2 instances, including choosing the operating system, software, and resource allocation. Instances are resizable, allowing vertical scaling, i.e. giving an instance more memory and more CPU.

**Networking Control** : Users can configure networking aspects, such as accessibility and requests to the EC2 instances.

## Amazon EC2 Instance Types

AWS offers different EC2 instance types optimised for specific tasks. These instance types fall into categories like general purpose, compute-optimized, memory-optimized, accelerated computing, and storage-optimized. Each type provides a unique combination of CPU, memory, storage, and networking capacity to suit different application needs.

**Memory-optimized** : In computing, memory serves as a temporary storage area that stores data and instructions necessary for the CPU to execute tasks. When a program or application is launched, it is loaded from storage into memory, granting the CPU immediate access.

These instances cater to workloads with significant memory requirements, ensuring excellent performance and responsiveness, such as tasks demanding substantial data preloading, such as high-performance databases or real-time processing of large unstructured data.

**General purpose** instances provide a balance of computing, memory, and networking resources.

**Compute-optimized** instances are ideal for **compute-bound applications** that benefit from high-performance processors.

**Memory-optimized** instances are designed to deliver fast performance for workloads that **process large datasets in memory**.

Accelerated computing instances use hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs, i.e. for accelerated **computing optimized for specific calculations**.

Storage-optimized instances are designed for workloads that require **high, sequential read and write access to large datasets** on local storage.

## Amazon EC2 Pricing

**On-Demand** : This option charges you based on the duration your instance runs, either per hour or per second. It's suitable for getting started, and testing workloads, and doesn't require long-term commitments or upfront payments. Kw: **can't tolerate disruption**

**Savings Plan (EC2, Lambda, Fargate, SM)**: Offers reduced prices in exchange for committing to a specific amount of usage measured in dollars per hour for one or three years. Up to a 72% savings. Use when usage is mostly steady and may **require changes to instances** from time to time (more flexible). You don't specify (type, OS, size…) upfront.

**Reserved Instances (EC2 only)**: Suited for steady-state or predictable workloads. Up to a 75% discount. Payment options include all upfront, partial upfront or no upfront. **Standard** where you specify instance type and size, operating system, and tenancy. **Convertible** if you need to change the number of EC2 instances, or need to run your EC2 instances in different Availability Zones or different instance types.

With SPs and RIs, you pay even if the instances are not running.

**Spot Instances** : Provide spare EC2 computing capacity at up to 90% off the On-Demand price. However, AWS can reclaim these instances with a two-minute warning, so they are suitable for workloads that can tolerate interruptions, such as batch processing.

**Dedicated Hosts** : These are physical hosts dedicated solely to your EC2 instances, often used to meet compliance requirements.

## Scalability

Scalability in AWS involves designing your system to adapt automatically to changing demand, ensuring that you pay only for the resources you use and never run out of computing capacity. To achieve automatic scaling, you can utilize the AWS service called Amazon EC2 Auto Scaling.

**Amazon EC2 Auto Scaling** dynamically adds or removes EC2 instances based on fluctuations in application demand. This automated scaling ensures better application availability and responsiveness. There are two approaches within Amazon EC2 Auto Scaling: dynamic scaling, which reacts to real-time demand changes, and predictive scaling, which schedules EC2 instances based on predicted demand

When setting up an Auto Scaling group, you can specify the **minimum** , desired, and maximum number of EC2 instances. The minimum capacity ensures at least MC instances are always running, while the desired capacity can be set higher to meet your application's requirements.

If you don't specify the desired capacity, it defaults to the minimum capacity. You can also set a maximum capacity to limit scaling in response to increased demand, ensuring cost control.

By using Amazon EC2 Auto Scaling, you pay only for **the instances you use when you use them** , creating a cost-effective architecture that maintains the best customer experience while reducing expenses.

## Elastic Load Balancing

Elastic Load Balancing is the AWS service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances.

A load balancer acts as a single point of contact for all incoming web traffic to your Auto Scaling group. This means that as you add or remove Amazon EC2 instances in response to the amount of incoming traffic, these requests route to the load balancer first. Then, the requests spread across multiple resources that will handle them. For example, if you have multiple Amazon EC2 instances, Elastic Load Balancing distributes the workload across the multiple instances so that no single instance has to carry the bulk of it.

When your EC2 fleet auto-scales out, as each instance comes online, the auto-scaling service just lets the Elastic Load Balancing service know that it's ready to handle the traffic, and off it goes. Once the fleet scales in, ELB first stops all new traffic, and waits for the existing requests to complete, to drain out. Once they do that, then the auto-scaling engine can terminate the instances without disruption to existing customers.

Although ELB and Amazon EC2 AS are separate services, they work together to help ensure high performance and availability.

ELB is not only used for external traffic but can be used to also coordinate communication between the front end and the back end of a service.

## Messaging and Queuing

Applications consist of multiple components that communicate to transmit data and fulfill requests. In a monolithic application, these components are tightly coupled, including databases, servers, user interfaces, and business logic. If one component fails, it can lead to the failure of other components and potentially the entire application.

To ensure application availability in the event of component failures, a microservices approach can be adopted. In a microservices architecture, application components are loosely coupled, allowing other components to continue working even if one fails.

When designing applications on AWS, a microservices approach involves using services and components that fulfill different functions. Amazon Simple Notification Service (Amazon SNS) and Amazon Simple Queue Service (Amazon SQS) are two services that facilitate application integration.

Amazon SNS is a publish/subscribe service where a publisher sends messages to subscribers, which are split into different categories. Subscribers in Amazon SNS can be web servers, email addresses, etc. Messages can be push notifications, emails, http requests…

Amazon Simple Queue Service (Amazon SQS) is a message queuing service, using which, you can send, store, and receive messages between software components, without losing messages or requiring other services to be available. In Amazon SQS, an application sends messages into a queue. A user or service retrieves a message from the queue, processes it, and then deletes it from the queue. kw: **decoupling** , **asynchronous** , **independent scaling**

## Serverless Computing

Serverless computing allows you to run code on servers **without the need to provision** or manage those servers. This approach allows you to focus on innovation rather than server maintenance.

AWS Lambda is a serverless computing service on AWS that allows you to run code without managing servers, but not suited for functions running for more than 15 minutes (more suitable for simple functions). It supports various application types, from data processing to web applications. Lambda automatically scales your code, and you pay only for the requests and duration. It uses functions, triggers, and events to execute code in response to events. This cost-effective service bills for number of requests and the code runtime only rounded up to milliseconds.

Containers provide a way to package your application's code and dependencies into a single object, ensuring consistent environments across deployments. You can use containers to manage processes and workflows securely and reliably. Container orchestration services like Amazon Elastic Container Service (Amazon ECS) and Amazon Elastic Kubernetes Service (Amazon EKS) help deploy, manage, and scale containerized applications.

Amazon ECS is a container management system that supports Docker containers, allowing you to launch and stop Docker-enabled applications using API calls.

Amazon EKS is a fully managed service for running Kubernetes on AWS, enabling you to deploy and manage containerized applications at scale with easy updates.

ECS and EKS are suited for microservices designed applications that require low risks when deployed in production.

AWS Fargate is a serverless compute engine for containers that works with both Amazon ECS and Amazon EKS. With Fargate, you don't need to provision or manage servers; AWS takes care of server infrastructure, allowing you to focus on application development and paying only for the required resources to run your containers.

You never pay for idle resources.

# Module 3: Global Infrastructure and Reliability

## Introduction

AWS prioritizes high availability and fault tolerance in its global infrastructure design. Unlike relying on a single data center, AWS operates in multiple regions worldwide. This approach ensures that even if one region faces issues such as power outages or natural disasters, AWS services and applications remain accessible and functional in other regions. This commitment to high availability is a core aspect of AWS's service delivery, offering businesses reliability and resilience in their cloud operations.

## AWS Global Infrastructure

AWS's global infrastructure is designed with high availability and fault tolerance in mind, offering multiple Regions around the world. Within each Region, AWS operates multiple data centers equipped with the necessary compute, storage, and services. These Regions are interconnected via a high-speed fiber network, allowing seamless access to resources across the globe.

Businesses have the flexibility to choose the Region in which they want to operate. Each Region is isolated from others, ensuring data remains within the chosen Region unless explicitly moved. This approach aligns with regional data sovereignty laws and regulations, enhancing security.

When selecting a Region, businesses should consider four key factors:

1. Compliance: Compliance requirements may dictate the choice of Region, ensuring data stays within specific boundaries.

1. Proximity: The physical distance to your customer base impacts latency, making it essential to locate your resources close to your target audience.

1. Feature Availability: Some Regions may have certain AWS features before others due to ongoing service expansion. Consider feature availability when choosing a Region.

1. Pricing: Operating costs can vary between Regions due to factors like taxes and operating expenses. Budget considerations may influence your Region selection.

These factors help businesses make informed decisions about the AWS Region that best suits their needs, ensuring high availability, compliance, and cost-effectiveness.

### Availability Zones

AWS addresses the issue of single-location dependency and the need for disaster recovery by designing its infrastructure with multiple Availability Zones (AZs) within each AWS Region. **Each AZ consists of one or more separate data centers** with redundant power, networking, and connectivity.

The AZs are intentionally geographically separated, ensuring that events like natural disasters do not impact multiple AZs simultaneously. By distributing resources across different AZs, AWS enhances the availability and fault tolerance of applications.

For high availability, AWS recommends (manually) deploying resources **across at least two AZs** within a Region **unless it's a Region-scoped service** , in which case, **AWS automatically performs actions** to increase data durability and availability. This practice helps ensure redundancy and resilience to potential failures. In case of a disaster affecting one AZ, applications can continue running in the other AZs.

For example, the Elastic Load Balancer (ELB) is a regional construct that can distribute traffic to EC2 instances across all AZs, enhancing the availability of applications without requiring additional configuration.

This regional approach to infrastructure and services ensures high availability and fault tolerance for applications, contributing to a robust and reliable AWS environment.

## Edge locations

AWS provides a global infrastructure designed to help businesses efficiently serve customers around the world. This infrastructure includes key components like Regions, Availability Zones (AZs), Content Delivery Networks (CDNs), and services like Amazon CloudFront.

**Regions** : AWS Regions are geographically isolated areas containing a collection of data centers and resources. Each Region operates independently and is isolated from others to maintain data sovereignty and compliance with local laws.

**Availability Zones** (AZs): AZs are physically separated data centers within a Region, designed to provide redundancy and fault tolerance.

**Amazon CloudFront** : Amazon CloudFront is a content delivery network (CDN) service that accelerates content delivery to users around the world. It uses **Edge locations** strategically positioned worldwide to reduce latency and improve transfer speeds. An edge location is a site that Amazon CloudFront uses to store cached copies of your content closer to your customers for faster delivery. AWS Edge locations also support other services like Amazon Route 53, a domain name service (DNS) for directing users to the correct web locations with low latency.

**AWS Outposts** : For businesses with specific requirements that necessitate AWS functionality within their own data centers, AWS offers AWS Outposts, a service that enables you to run infrastructure in a hybrid cloud approach. AWS installs a mini Region inside a customer's data center, providing access to AWS services while remaining isolated within the customer's premises.

## How to Provision AWS Resources

### Part 1

In AWS, interactions with services are primarily done through APIs (Application Programming Interfaces). Here's an overview of how you can interact with AWS services:

**AWS Management Console** : The AWS Management Console is a browser-based interface that allows you to visually manage AWS resources. It's suitable for getting started, learning about AWS services, creating test environments, viewing billing information, and managing non-technical aspects. While it's user-friendly, it's not ideal for large-scale automation and scripting.

**AWS Command Line Interface** (CLI): The AWS CLI is a powerful tool that lets you interact with AWS services through your computer's terminal or command prompt. You can use it to execute API commands by writing scripts or running commands manually. This approach is scriptable, repeatable, and less error-prone than manual actions through the console. Automation is a key benefit, and you can schedule scripts or trigger them based on specific events. Authentication requires an Access key ID and a Secret access key.

**AWS Software Development Kits** (SDKs): AWS provides SDKs for various programming languages, making it easy for developers to interact with AWS services programmatically. Instead of working directly with low-level APIs, developers can use these SDKs to integrate AWS services into their applications seamlessly. It simplifies resource management and reduces the need for manual actions.

Other Tools: AWS offers additional tools like **AWS CloudFormation** , which allows you to define infrastructure as code (IAC) using templates. These templates can be used to provision and manage AWS resources consistently and predictably. Other third-party tools and services can also be integrated with AWS to enhance automation and resource management.

While the AWS Management Console is a valuable starting point for learning and exploration, as your AWS usage grows and becomes more complex, transitioning to CLI, SDKs, and automation tools becomes crucial to ensure efficiency, consistency, and scalability in managing your AWS resources.

### Part 2

**AWS Elastic Beanstalk** : This service simplifies the deployment and management of applications. You provide your application code and configurations, and Elastic Beanstalk takes care of provisioning and managing the underlying infrastructure, including EC2 instances, scaling, and load balancing. It's great for developers who want to focus on application development without dealing with infrastructure details.

_One major difference compared to AWS Fargate is that Elastic Beanstalk builds your application for you. You just upload code, and Elastic Beanstalk does the rest. With Fargate, however, you have to create a container image for your application first._

**AWS CloudFormation** : CloudFormation is an **infrastructure-as-code** tool that allows you to define AWS resources using templates (JSON or YAML). With CloudFormation, you describe your desired resources and their configurations in a declarative manner. CloudFormation then automates the provisioning of these resources, ensuring consistency across environments, accounts, and regions. It's a powerful choice for creating automated, repeatable deployments and managing complex AWS architectures.

# Module 4: Networking

## Introduction

Amazon Virtual Private Cloud (VPC) allows you to create a logically isolated section of the AWS Cloud. You can launch AWS resources in this virtual network, defining public-facing resources with internet access, typically for user interaction, and private resources without internet access, typically for backend services.

A VPC **peering connection** is a networking connection between two VPCs that enables you to route traffic between them using private IP addresses. Instances in either VPC can communicate with each other as if they are within the same network.

## Connectivity to AWS

Amazon Virtual Private Cloud (Amazon VPC) is a service that establishes boundaries around AWS resources to prevent unrestricted network traffic between them. It allows you to create an isolated section of the AWS Cloud, where you can define a virtual network and organize resources into subnets. An internet gateway is used to allow public internet traffic into the VPC. It's not the VPC that makes the resources secure, it just establishes boundaries around AWS resources to prevent unrestricted network traffic between them.

Network Address Translation, NAT, Gateway (NGW) allows instances with no public IPs to access the internet. It is a highly available, managed network component that enables instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating connections with those instances.

![](RackMultipart20231110-1-3kgbr9_html_ee53467c10d6a21.png)

Suppose you have a VPC with only private resources. In that case, you can use a virtual private gateway, which works like a VPN connection (encrypted over the general internet), adding an extra layer of protection to internet traffic before it enters the VPC (as if it was coming from a specific verified network). This ensures traffic comes from approved networks, but it still uses the internet to get there.

![](RackMultipart20231110-1-3kgbr9_html_8aa35fd136336b6a.png)

AWS Direct Connect is a service that provides a dedicated private connection between your data center and a VPC (exclusive fiber used by you and you alone). This dedicated connection, where all network traffic between the corporate data center and VPC flows, reduces network costs and increases bandwidth for data traffic between your corporate data center and VPC. through this dedicated private connection.

![](RackMultipart20231110-1-3kgbr9_html_51fc6a8be0b7859a.png)

## Subnets and Network Access Control Lists

**Network ACLs** : These are compared to passport control officers and they sit inside the VPC at the **border of a subnet**. They evaluate whether incoming or outgoing packets have the necessary permissions to cross subnet boundaries within the VPC. They operate in a **stateless** manner (no memory of who passed earlier, in and out are two streams), checking every packet that crosses the border, i.e. going in and going out are two different streams. By default, they allow all inbound and outbound messages.

**Security Groups** : These are likened to doormen that sit on the **boundary of specific components inside a subnet** , e.g. individual EC2 instances. By default, they block all incoming traffic and allow all outbound traffic, and you must specify the rules for allowing specific types of traffic. Security Groups are **stateful** (in and out are one stream), meaning they recognize previously allowed traffic, making it easier for return traffic, i.e. packets that are sent out and returning can cross a security group check since the SG remembers what passed through it earlier, even if it blocks all inbound traffic by default.

In SGs, there is no explicit deny: no explicit accept -\> deny

![](RackMultipart20231110-1-3kgbr9_html_61ac7997e0a5a091.png)

VPC Endpoints: allow instances to connect to public AWS services without the need of a gateway

Gateway Endpoint: to connect to public services through a gateway (S3, DynamoDB)

Interface Endpoint: to connect to public services other than S3 and DynamoDB

## Global Networking

One crucial aspect of the interaction with AWS infrastructure, particularly websites hosted on AWS, is DNS, a translation service translating user-friendly website addresses into IP addresses that computers understand. AWS offers a service called Route 53 for managing domain names. Route 53 also provides domain registration services, allowing users to purchase and manage domain names directly through AWS.

#


# Module 5: Storage and Databases

## Instance Stores and Amazon Elastic Block Store (EBS)

Amazon EC2 instances offer both instance stores and Amazon Elastic Block Store (EBS) for storage needs.

Instance stores are like physical hard drives, providing **temporary** block-level storage (meaning the data is treated as being composed on many blocks, and not as one entity as with object storage) physically attached to the host computer of an EC2 instance, and lives in one, and the same AZ as the EC2 instance. However, data in the instance store is volatile, meaning it **gets deleted** when the EC2 instance is terminated or stopped. AWS recommends using instance stores for temporary data that you don't require long-term. The IS persists if the instance is rebooted.

On the other hand, Amazon Elastic Block Store (EBS) offers block-level storage volumes for Amazon EC2 instances. Data on EBS volumes **persists** even when the EC2 instance is terminated or stopped. To use EBS volumes, you define the size and type, provision them, and attach them to your EC2 instance. This makes them suitable for data that needs to be retained. It's crucial to back up your EBS data regularly using **incremental backups** known as EBS snapshots. Unlike **full backups** , EBS snapshots only save changed data since the last snapshot, ensuring efficient storage and data protection.

**AWS Storage Gateway** : to connect on-premise storage to AWS storage + migration

## Amazon Simple Storage Service (Amazon S3)

Data is stored as objects in buckets, similar to files on a hard drive and directories being the buckets. There is no tree structure with buckets, and every file has a unique identifier. However, you can emulate one by using prefixes, which the SDKs could use.

Amazon S3 supports an unlimited amount of objects up to 5 terabytes in size each, and allows versioning to safeguard against accidental deletion or overwriting. Amazon S3 doesn't require manual provisioning and is replicated over AZs in a region, region-level service.

Access permissions can be configured using **policies** to restrict who can view or access objects, and data can be moved between different storage classes or tiers, each designed for specific use cases:

S3 Standard:

- Designed for frequently accessed data.
- Stored in a minimum of three Availability Zones for high availability.
- Suitable for websites, content distribution, and data analytics.
- Higher cost.

S3 Standard-Infrequent Access (S3 Standard-IA):

- For infrequently accessed data with high availability needs.
- Lower storage cost and higher retrieval cost compared to S3 Standard.
- Same availability as S3 Standard.

S3 One Zone-Infrequent Access (S3 One Zone-IA):

- Data stored in a single Availability Zone for cost savings.
- Suitable for data that can be recreated in case of an Availability Zone failure.

S3 Intelligent-Tiering:

- Ideal for data with **unknown or changing access patterns**.
- Requires a monthly monitoring and automation fee.
- Automatically moves objects to the appropriate tier based on usage.

S3 Glacier Instant Retrieval:

- Designed for archived data with immediate access needs.
- Objects can be retrieved within milliseconds, similar to S3 Standard.

S3 Glacier Flexible Retrieval:

- Low-cost storage for data archiving.
- Retrieval of objects within minutes to hours.
- Suitable for long-term data archiving.

S3 Glacier Deep Archive:

- Lowest-cost storage for archiving data.
- Objects can be retrieved within 12 hours.
- Ideal for long-term retention and infrequent access.

S3 Outposts:

- Create S3 buckets on AWS Outposts for on-premises environments.
- Durable and redundant storage for local devices and servers.
- Meets data residency and performance needs for on-premises applications.
- These storage classes offer flexibility and cost-effectiveness to match specific business requirements, access patterns, and budget considerations.

### S3 vs EBS

S3: when using complete objects or doing only occasional changes.

EBS: when doing complex read, write, and change functions.

## Amazon Elastic File System (Amazon EFS) **Linux-only**

Amazon EFS is a managed file system service that simplifies shared file systems for businesses. It's handy for scenarios where multiple servers need access to shared data:

Amazon EFS:

- Managed (Linux) file system (not a blank HD), i.e. has structure.
- Supports shared file storage for **multiple instances concurrently**.
- **Scales automatically** based on the data you store without manual provisioning.
- **Regional resource** , allowing any EC2 instance within the AWS Region to access it.

Amazon EBS:

- Slower than Instance stores because it is not physically connected
- Block-level storage volumes.
- Attachable to (mosly only one) EC2 instances and bound to a specific **Availability Zone** (AZ level), i.e. needs to be in the same AZ as the EC2 instances.
- Replicated over servers in an AZ
- Acts like a hard drive, suitable for storing files, running databases, or hosting applications.
- Requires **manual provisioning** ; it doesn't automatically scale when you reach capacity.

Amazon FSx: file system for Windows

Amazon FSx Lustre: fpr apps requiring high distribution

## Amazon Relational Database Service (Amazon RDS)

In a relational database, data is stored in a way that relates it to other pieces of data. I.e. **structured data**. Each record in the database would include data for a single item, and data can be connected across multiple tables. Relational databases use structured query language (SQL) to store and query data. This approach allows data to be stored in an easily understandable, consistent, and scalable way.

Amazon RDS offers automated features such as **patching** , **backups** , (synchronous and asynchronous) **redundancy** , **failover** , and **disaster recovery** , and also supports **manual snapshots**.

On the exam, asynchronous replications are related to Read replicas, whereas synchronous replications are related to multi-AZ scenarios.

Amazon Aurora is one cloud-native, enterprise-class RDS engine that is a high-performance **relational** database. It offers faster speeds compared to standard MySQL and PostgreSQL databases. It helps reduce costs by optimizing input/output operations while maintaining reliability. Amazon Aurora offers built-in security, **serverless** compute, up to 15 read replicas, automated multi-Region replication, and integrations with other AWS services. It replicates data across three Availability Zones for workloads requiring **high availability** and offers continuous backups to Amazon S3, ensuring data **resilience**.

## Amazon DynamoDB

Amazon DynamoDB is a serverless, highly scalable, and high-performance NoSQL database. It operates without the need to manage the underlying infrastructure. In DynamoDB, data is organized into tables, with items having attributes. The system handles scaling, storage **redundancy across AZs** , and data mirroring. It offers millisecond response times and is well-suited for workloads with many users.

Unlike traditional SQL databases, DynamoDB doesn't use SQL and offers a **flexible schema** (not every item in the table has to have the same attributes). Adding and removing attributes from items as needed makes it suitable for datasets with varying attributes. While SQL queries are complex, DynamoDB queries focus on a subset of designated key attributes within a single table. DynamoDB's design allows quick response times and exceptional scalability, making it ideal for specific use cases.

DynamoDB bills by requests and size of data per request.

## Amazon Redshift = column-based

When businesses require **historical data analysis** , often exceeding the capabilities of high-speed, real-time databases, data warehouses become crucial. These data warehouses specialize in handling vast historical analytics data, particularly for business intelligence purposes. Data warehouses, like Amazon Redshift, are the ideal solution for such business intelligence.

Amazon Redshift offers data warehousing as a service with massive scalability, supporting nodes in multiple petabyte sizes. It integrates with Amazon Redshift Spectrum, enabling queries against exabytes of unstructured data in data lakes. Redshift incorporates innovative technologies, providing up to 10 times better performance compared to traditional databases for business intelligence workloads. Redshift simplifies the process with a single API call, reducing wait times and allowing more time for gaining insights.

Redshift also has a serverless option.

## AWS Database Migration Service (AWS DMS)

AWS DMS is a service designed to facilitate the migration of existing databases to the AWS cloud efficiently and securely. DMS allows you to migrate data from a source database to a target database, while the source database **remains fully operational** during the migration. Notably, the source and target databases do not need to be similar, offering flexibility.

**Homogeneous Migrations** : In these migrations, the source and target databases are similar, such as MySQL to Amazon RDS for MySQL. Since the **schema structures** , **data types** , and **database code** are compatible between the source and target, the process is relatively straightforward. You create a **migration task** with connections to the source and target databases and initiate the migration.

**Heterogeneous Migrations** : These migrations involve source and target databases of different types, which requires a two-step process. Firstly, you use the AWS Schema Conversion Tool to convert the **source schema and code** to match that of the target database. Subsequently, AWS DMS migrates **data** from the source database to the target database.

DMS use cases:

Development and Test Database Migrations: Migrating a copy of a production database to development or test environments without affecting production users.

Database Consolidation: Combining multiple databases into a single central database for improved efficiency.

Continuous Database Replication: for continuous data replicationز

## Additional database services

Amazon DocumentDB is a document database service that supports MongoDB (a document database program) workloads.

Amazon Neptune is a graph database service that you can use to build and run applications that work with highly connected datasets, such as recommendation engines, fraud detection, and knowledge graphs.

Amazon Quantum Ledger Database (Amazon QLDB) is a ledger database service that is immutable and tracks everything so you can use to review a complete history of all the changes made to your application data.

Amazon Managed Blockchain is a service to create and manage blockchain networks with open-source frameworks.

Amazon ElastiCache is a service that adds caching layers on top of your databases to help improve the read times of common requests for real-time performance and low latency.

Amazon DynamoDB Accelerator (DAX) is an in-memory cache for DynamoDB that helps improve response times from single-digit milliseconds to microseconds.

#


# Module 6: Security

## AWS Shared Responsibility Model

In AWS, security is a shared responsibility between AWS and the customer. AWS is responsible for securing the physical infrastructure and certain layers, while customers are responsible for securing their data, applications, and the operating system on top of that infrastructure.

### AWS Responsibilities:

Physical layer security: AWS ensures the security of the data centers.

Network and hypervisor: AWS has robust security measures for its network and hypervisor infrastructure.

Third-party audits: AWS undergoes third-party audits to provide customers with compliance documentation.

### Customer Responsibilities:

Operating system (OS): Customers have full control and responsibility for the OS, including patching and maintenance.

Applications: Customers are responsible for the applications they run on the OS.

Data: Customers have complete control over their data, deciding who can access it and managing access rights.

The customers have exclusive access to their OS and data. AWS cannot access or deploy patches to customer OS instances. The customer's operations team is responsible for patching the OS. AWS can provide notifications of vulnerabilities but cannot directly apply patches.

Customers also have the flexibility to determine access to their data, and AWS provides tools for customers to manage data access, including options for encryption and security settings.

### Shared Responsibilities:

Controls which apply to both the infrastructure layer and customer layers, but in completely separate contexts or perspectives. In a shared control, AWS provides the requirements for the infrastructure and the customer must provide their own control implementation within their use of AWS services:

Patch Management – AWS is responsible for patching and fixing flaws within the infrastructure, but customers are responsible for patching their guest OS and applications.

Configuration Management – AWS maintains the configuration of its infrastructure devices, but a customer is responsible for configuring their own guest operating systems, databases, and applications.

Awareness & Training - AWS trains AWS employees, but a customer must train their own employees.

## User Permissions and Access

IAM is a service that enables secure management of access to AWS services and resources.

AWS Account **Root User** : When creating an AWS account, you start with a root user with complete access to all AWS services and resources. This is accessed by signing in with the email address and password that were used to create the account. The root also has an access key and a secret access key. Use this account to create an IAM user with admin controls, and operate other accounts using it instead of the root user.

IAM **Users** : IAM users represent individuals or applications interacting with AWS services. They **initially have no permissions** and must be explicitly granted access to specific actions or resources. The best practice is to create individual IAM users for **each person** needing access for added security. Access keys are used to authorize requests.

IAM **Policies** : IAM policies are documents that allow or deny permissions to AWS services and resources. These policies customize users' access levels. The **principle of least privilege** is recommended to prevent users from having unnecessary permissions. This is used for authentication (verify you are who you claim you are) and authorisation (whether you have permission to perform a certain action) purposes.

AWS Policy Simulator: test and troubleshoot IAM- and resource-based policies.

IAM **Groups** : IAM groups are collections of IAM users. Assigning an IAM policy to a group grants specified permissions to all users within that group. This simplifies permission management and aids in adjusting permissions when roles change.

IAM **Roles** : IAM roles allow **temporary** access to permissions. Users, applications, or **services** (e.g. when an EC2 instance wants to communicate with an S3 bucket) must be granted permissions to assume a role. When a role is assumed, all previous permissions are abandoned in favor of the role's permissions. IAM roles are ideal for temporary access to services or resources. They can also be used to channel an Identity Provider system (the business's own credential system) to the AWS account instead of creating a new user for each employee.

## AWS Organizations

AWS Groups and AWS Organizations serve different purposes in AWS account management:

AWS IAM Groups:

**Purpose** : AWS Groups are used to group and manage IAM users within a single AWS account. They are primarily for organizing users and simplifying permission management.

**Use Case** : You can create groups like "Developers," "Admins," or "Managers" and assign IAM policies to these groups, which apply to all users within the group. This makes it easier to manage permissions for users with similar roles.

**Scope** : AWS Groups are confined to a single AWS account.

AWS Organizations:

**Purpose** : AWS Organizations is a service designed for managing multiple AWS accounts in a hierarchy. It enables you to consolidate billing, apply policies across multiple accounts, and streamline the management of multiple AWS accounts.

**Use Case** : AWS Organizations is used when you have multiple AWS accounts for different teams, departments, or projects, and you want to manage them collectively. You can create **Organizational Units** (OUs) (HR, IT,…) to structure your accounts, apply **Service Control Policies** (SCPs) to enforce access and security policies across accounts or OUs, and link accounts for billing purposes.

**Scope** : AWS Organizations spans multiple AWS accounts and is used to centralize management, billing, and policy enforcement across those accounts.

OUs help isolate workloads or applications with specific security or regulatory requirements. For example, you can create an OU for accounts adhering to certain regulatory standards and apply a policy to restrict access to non-compliant AWS services.

## Compliance

AWS Artifact is a service that offers access to security and compliance documents, as well as select online agreements. It consists of two main sections:

AWS Artifact **Agreements** : This section includes agreements with the customers related to AWS services.

AWS Artifact **Reports** : It provides access to compliance reports and regulations, including AWS ISO certifications, PCI reports, and SOC reports.

Additionally, AWS offers a Customer Compliance Center, which contains resources for learning about AWS compliance and an auditor learning path designed for those in auditing, compliance, and legal roles to understand how to demonstrate compliance using AWS Cloud.

##


## Denial-of-Service Attacks

A denial-of-service ( **DoS** ) attack is an intentional effort to render a website or application inaccessible to users by overwhelming it with excessive traffic, rendering it unresponsive.

In a distributed denial-of-service ( **DDoS** ) attack, multiple sources, including potentially a group of attackers or a single attacker using multiple infected computers (bots), target a website or application with excessive traffic to disrupt its availability. AWS Shield (Standard and Advanced) is a service that can help mitigate the impact of DoS and DDoS attacks on your applications.

## Additional Security Services

AWS **Key Management Service** (AWS KMS) allows for secure encryption operations using cryptographic keys for data protection at rest and in transit.

AWS **WAF** is a web application firewall that **monitors and filters** network requests for web applications. It can be used against DDoS attacks.

Amazon **Inspector** automates security assessments, identifying vulnerabilities and deviations from best practices.

Amazon **GuardDuty** provides intelligent threat detection by continuously monitoring network and account activity within your AWS infrastructure, offering recommendations for remediation.

# Module 7: Monitoring and Analytics

## CloudWatch

Amazon **CloudWatch** is a web service for monitoring and managing metrics, allowing automatic creation of **performance graphs** over time. It supports the creation of **alarms** to **trigger** actions based on metric values exceeding or falling below predefined thresholds. CloudWatch's dashboard provides a centralized view for monitoring various resource metrics and is customizable for different business needs and resources.

This allows you to:

- Have access to all your metrics from a central location.
- Get visibility across your applications, infrastructure, and services.
- Reduce mean time to resolution, or MTTR, and improve total cost of ownership, or TCO.
- Drive insights to optimize applications and operational resources.

## AWS CloudTrail (basically a log-everything tool)

AWS CloudTrail records API calls in your account, providing a history of user activity and resource-related actions. It offers details about the caller's identity, time, and source IP address for each API call. Events are updated within 15 minutes and can be filtered by criteria like time, user, and resource type. CloudTrail helps track and audit AWS actions, making it useful for identifying the source and details of specific events, even enabling automatic detection of unusual activities through CloudTrail Insights.

## AWS Trusted Advisor

AWS Trusted Advisor is a web service that evaluates your AWS environment and offers real-time recommendations aligned with AWS best practices.

It assesses your environment in five categories: **cost optimization** , **performance** , **security** , **fault tolerance** , and **service limits**. Trusted Advisor suggests actions and provides additional resources for each category, helping at various deployment stages, from workflow creation to ongoing application and resource enhancements.

The Trusted Advisor dashboard on the AWS Management Console presents checks with green checks (no problems detected), orange triangles (recommended investigations), and red circles (recommended actions) for each category.

# Module 8 Pricing and Support

## AWS Free Tier

The AWS Free Tier enables you to begin using certain services without having to worry about incurring costs for the specified period. Three types of offers are available: Always Free, 12 Months Free, and Trials.

## How AWS pricing works

AWS offers a range of cloud computing services with pay-as-you-go pricing.

Pay for **what you use** : for each service, you pay for exactly the amount of resources that you actually use, without requiring long-term contracts or complex licensing.

Pay less **when you reserve** : some services offer reservation options that provide a significant discount compared to On-Demand Instance pricing.

Pay less with **volume-based discounts when you use more** : some services offer tiered pricing, so the per-unit cost is incrementally lower with increased usage.

The AWS **Pricing Calculator** (this is different from Cost Explorer) lets you explore AWS services, create an estimate for the cost of your use cases on AWS (based on the used specs), and organize your AWS estimates by groups.

## Billing Dashboard

Use the AWS Billing & Cost Management dashboard to pay your AWS bill, monitor your usage, and analyze and control your costs.

## Consolidated Billing

The **consolidated billing** feature of AWS Organizations enables you to receive a single bill for all AWS accounts in your **organization** so you can easily track the combined costs of all the linked accounts in your organization.

On your monthly bill, you can review itemized charges incurred by each account to enable greater transparency into your organization's accounts while still maintaining the convenience of receiving a single monthly bill.

Another benefit of consolidated billing is the ability to share bulk discount pricing, Savings Plans… across the accounts in your organization, when one account does not have enough monthly usage to qualify for a discount but the accounts combined qualify for a benefit that applies across all accounts in the organization.

## AWS Budgets

In AWS Budgets, you can create budgets to plan your service usage, service costs, and instance reservations, review how much cost your predicted AWS usage will incur by the end of a period, and set custom alerts when your usage exceeds (or is forecasted to exceed) the budgeted amount.

## AWS Cost Explorer

AWS Cost Explorer is a tool that lets you visualize, understand, and manage your AWS costs and usage over time. It also includes a default report of the costs and usage for your top five cost-accruing AWS services. _It is a__historical analysis tool_.

By analyzing your AWS costs over time, you can make informed decisions about future costs and how to plan your budgets.

## AWS Cost and Usage Reports

AWS CUR provides the most detailed billing data of any AWS cost management tool, including information about usage of AWS services, such as the number of hours of usage, data transfer, as well as cost information, including total costs and costs for each service, account, and region. It is more granular than AWS Cost Explorer.

## AWS Support Plans

AWS offers various Support plans, including **Basic** , **Developer** , **Business** , **Enterprise On-Ramp** , and **Enterprise** Support:

Basic Support: Free for all AWS customers, offering access to documentation, billing support, and limited AWS Trusted Advisor checks. It includes the Personal Health Dashboard that is the authoritative data source for events and changes affecting your AWS cloud resources.

Developer, Business, Enterprise On-Ramp, and Enterprise Support: These paid plans include all Basic Support features, unlimited technical support cases, and additional benefits.

**Developer Support** : Offers best practice guidance, diagnostic tools, and building-block architecture support to help users combine AWS services effectively. Unlimited number of cases that can be opened.

**Business Support** : Includes use-case guidance, all AWS Trusted Advisor checks, and limited support for third-party software + AWS support API

**Enterprise On-Ramp Support** : Offers access to Technical Account Managers (TAMs), a Cost Optimization workshop, a Concierge support team, and various support automation tools with a 30-minute response time for critical issues.

**Enterprise Support** : Provides a designated TAM, Operations Reviews, training, game days, full access to proactive services, consultative review, and infrastructure event management, with a 15-minute response time for critical issues.

The TAM acts as your primary AWS contact, providing expert guidance, helping design solutions, optimizing cost and performance, and giving access to AWS programs and experts, catering to specific company needs.

## AWS Marketplace

AWS Marketplace is a digital catalog that includes thousands of software listings from independent software vendors. You can use AWS Marketplace to find, test, and buy software that runs on AWS.

# Module 9 Migration and Innovation

## AWS Cloud Adoption Framework (AWS CAF)

Business Perspective: Aligns IT with business needs, creates a strong business case for cloud adoption, and ensures business and IT strategies are in sync.

People Perspective: Focuses on organization-wide change management, evaluates roles and skill gaps, and prioritizes training and staffing.

Governance Perspective: focuses on orchestrating your cloud initiatives while maximizing

organizational benefits and minimizing transformation-related risks, and managing cloud investments.

Platform Perspective: Provides principles and patterns for cloud solutions and workload migrations. It focuses on architectural models.

Security Perspective: Ensures the organization meets security objectives by structuring the selection and implementation of security controls.

Operations Perspective: Helps enable, run, and recover IT workloads, supporting the operations of the business. It defines current operating procedures and identifies process changes and training needs.

## Migration Strategies

When migrating applications to the cloud, there are six common migration strategies:

**Rehosting** : This strategy, also known as "lift-and-shift," involves moving applications to the cloud without making significant changes to them. It is often used for large legacy migrations when speed is essential.

**Replatforming** : Replatforming, or "lift, tinker, and shift," involves making minor optimizations to applications to gain cloud benefits without fundamentally altering their core architecture.

**Refactoring** / **Re-architecting** : Refactoring, or re-architecting, entails reimagining how an application is designed and developed, utilizing cloud-native features. It is driven by a need for added features, scalability, or performance that is challenging to achieve in the existing environment. This has the most initial cost.

**Relocating**

**Repurchasing** : This strategy involves shifting from a traditional software license model to a software-as-a-service (SaaS) model. For instance, migrating from an on-premises CRM system to Salesforce.com. This has the most upfront cost.

**Retaining** : This strategy involves keeping critical applications in their source environment, either because they require substantial refactoring before migration or because their migration can be postponed, or because they will be abandoned soon.

**Retiring** : Retiring is the process of decommissioning and removing applications that are no longer needed.

## AWS Snow Family

The AWS Snow Family is a collection of physical devices designed to transport large amounts of data into and out of AWS. These are sent to you, you put the data, and then send it back to AWS for them to upload your data. Some of them also have compute capabilities. It includes:

AWS **Snowcone** : This is a small, rugged, and secure edge computing and data transfer device with 14 TB of storage.

AWS **Snowball** : It offers two types of devices:

**Storage Optimized** : Suitable for large-scale data migrations and recurring transfer workflows. 80 TB HDD, and 28 TB SSD.

**Compute Optimized** : Designed for powerful computing tasks like machine learning and analytics. 80 TB HDD, and 1TB SSD.

AWS **Snowmobile** : This is an exabyte-scale data transfer service used to move extremely large amounts of data to AWS, 100 PB of storage.

## Innovation with AWS

AWS provides a vast range of services and capabilities for various business needs:

**Migrating to AWS** : You can migrate your existing infrastructure, even VMware-based, to AWS using services like VMware Cloud on AWS. It offers a seamless transition from on-premises to the cloud.

**Machine Learning and AI** : AWS offers an extensive suite of machine learning and AI services. You can use pre-trained AI services for various tasks, leverage Amazon **SageMaker** to build custom machine learning models, and utilize tools like Amazon **Lex** for interactive chatbots or Amazon **Textract** to extract data from documents.

**AWS DeepRacer** : This allows developers to experiment with **reinforcement learning** in a fun and interactive racing environment, making machine learning accessible to a wider audience.

**Internet of Things (IoT)**: AWS provides IoT services to enable connected devices to communicate globally, facilitating the development of IoT applications.

**AWS Ground Station** : It allows you to access satellite communication without the need to launch your own satellites, and you only pay for the satellite time you use.

# Module 10 The Cloud Journey

## The AWS Well-Architected Framework

**Operational Excellence** : This pillar focuses on running, monitoring, and continually improving systems, with key principles including "operations as code," documentation, and the ability to anticipate and recover from failures.

**Security** : It emphasizes protecting information, systems, and assets through best practices like automating security, applying security at all layers, and securing data in transit and at rest.

**Reliability** : This pillar relates to a system's ability to recover from disruptions, scale dynamically, and mitigate issues. It includes testing recovery procedures, horizontal scaling, and automated failure recovery.

**Performance Efficiency** : Performance efficiency involves using computing resources effectively to meet system requirements and maintaining efficiency as demands change. It encourages experimenting, using serverless architectures, and being able to scale globally.

**Cost Optimization** : Cost optimization focuses on delivering business value at the lowest cost by adopting a consumption model, analyzing expenditures, and leveraging managed services to reduce ownership costs.

**Sustainability** : Introduced in December 2021, this pillar is about improving sustainability by reducing energy consumption, setting goals, maximizing resource utilization, adopting efficient hardware and software, and reducing the environmental impact of cloud workloads.

##


##


## Other Services

Transit Gateway

Analytics:

- Amazon Athena: Serverless, interactive analytics service querying data in Amazon S3 using SQL.
- AWS Data Exchange: Find, subscribe to, and use third-party data in the cloud.
- Amazon EMR: Process large amounts of data using open-source tools.
- AWS Glue: Prepare and load data for analytics using ETL (extract, transform, load).
- Amazon Kinesis: Collect, process, and analyze real-time streaming data in a scalable fashion.
- Amazon Managed Streaming for Apache Kafka (Amazon MSK): Build and run applications that use Apache Kafka to process streaming data.
- Amazon OpenSearch Service: Deploy, operate, and scale Elasticsearch clusters to perform interactive analytics, real-time application monitoring, and website search.
- Amazon QuickSight: Business intelligence service to create visualizations, perform ad-hoc analyses, and quickly get business insights.

Application Integration:

- Amazon EventBridge: Serverless event-based bus to connect applications using data from your applications, SaaS, and AWS services.
- AWS Step Functions: Serverless visual workflow service to coordinate distributed applications and microservices.

Business Applications:

- Amazon Connect: Cloud-based contact center service for your customers.
- Amazon Simple Email Service (Amazon SES): Email sending and receiving service to keep in contact with their customers through email.

Cloud Financial Management:

- AWS Billing Conductor: Automate billing and cost management tasks.
- AWS Cost and Usage Report: Access comprehensive cost and usage information.

Compute:

- AWS Batch: Run batch computing workloads on the cloud.
- Amazon Lightsail: Build applications and websites fast with low-cost, **pre-configured** cloud resources.
- AWS Local Zones: Low-latency compute and storage closer to end-users.
- AWS Wavelength: Ultra-low latency for 5G applications.
- EC2 Image Builder: simplifies the building, testing, and deployment of Virtual Machine and container images for use on AWS or on-premises.

Containers:

- Amazon Elastic Container Registry (Amazon ECR): Store, manage, and deploy Docker container images.
- Amazon Elastic Container Service (Amazon ECS): Run and scale containerized applications.

Customer Engagement:

- AWS Activate for Startups: Resources and benefits for startups.
- AWS IQ: Get help from AWS Certified third-party experts.
- AWS Managed Services (AMS): Managed services to operate AWS infrastructure.
- AWS Support: Technical support plans for AWS customers.

Database:

- Amazon MemoryDB for Redis: In-memory database for Redis.

Developer Tools:

- AWS AppConfig: Application configuration management.
- AWS Cloud9: Cloud-based integrated development environment (IDE).
- AWS CloudShell: Browser-based shell command-line interface (CLI).
- AWS CodeArtifact: Secure, scalable, and cost-effective artifact management.
- AWS CodeBuild: Build and test code using pre-configured build environments.
- AWS CodeCommit: Store and manage code in private Git repositories.
- AWS CodeDeploy: Automate code deployments to any instance.
- AWS CodePipeline: Continuous delivery service for fast and reliable application updates.
- AWS CodeStar: Develop, build, and deploy applications on AWS.
- AWS X-Ray End User: Analyze and debug distributed applications.
- AWS OpsWorks: configuration management service to construct, manage, and operate a wide variety of application architectures, from simple web applications to highly complex custom applications.

Computing:

- Amazon AppStream 2.0: Stream desktop applications securely to any computer.
- Amazon WorkSpaces: Virtual desktops in the cloud.
- Amazon WorkSpaces Web: Access Amazon WorkSpaces from a web browser.

Frontend Web and Mobile:

- AWS Amplify: Develop and deploy mobile and web applications.
- AWS AppSync: Build data-driven apps with real-time and offline capabilities.
- AWS Device Farm: Test mobile apps on real devices in the cloud across a variety of devices and OSs.

Internet of Things (IoT):

- AWS IoT Core: Connect devices to the cloud.
- AWS IoT Greengrass: Local compute, messaging, and sync for devices.

Machine Learning:

- Amazon Comprehend: Natural language processing (NLP) service.
- Amazon Kendra: Enterprise search service.
- Amazon Lex: Build conversational interfaces using voice and text.
- Amazon Polly: Text-to-speech service.
- Amazon Rekognition: Image and video analysis service.
- Amazon Textract: Extract text and data from documents.
- Amazon Transcribe: Automatic speech recognition (ASR) service.
- Amazon Translate: Neural machine translation service.

Management and Governance:

- AWS Auto Scaling: Scale multiple resources automatically.
- AWS Compute Optimizer: Resource optimization recommendations.
- AWS Config: Track resource inventory and changes.
- AWS Control Tower: Set up and govern a secure, compliant multi-account environment.
- AWS Health Dashboard: Personalized view of AWS service health.
- AWS Launch Wizard: Simplify deployment of third-party applications.
- AWS License Manager: Manage software licenses.
- AWS Management Console: Web-based user interface for AWS services.
- AWS Resource Groups and Tag Editor: Create, manage, and view resource groups.
- AWS Service Catalog: Create and manage catalogs of IT services.
- AWS Systems Manager: Gain operational insights and take action on AWS resources.
- AWS Well-Architected Tool: Review and improve your workloads.

Migration and Transfer:

- AWS Application Discovery Service: Discover on-premises applications to plan migration.
- AWS Application Migration Service: Migrate applications to AWS.
- AWS Migration Hub: Track and manage application migrations.
- AWS Schema Conversion Tool (AWS SCT): Convert database schema to AWS.
- AWS Transfer Family: Move files to and from AWS.

Networking and Content Delivery:

- Amazon API Gateway: Create, deploy, and manage APIs.
- AWS Global Accelerator: Improve application availability and performance.
- AWS VPN: Securely connect to AWS resources.

Security, Identity, and Compliance:

- AWS Audit Manager: Simplify audit preparation and automate continuous monitoring by automating evidence collection, being auditing-friendly, and making it easier to demonstrate complianceæ.
- AWS Certificate Manager (ACM): Provision, manage, and deploy SSL/TLS certificates.
- AWS CloudHSM: Hardware security module (HSM) to protect sensitive data.
- Amazon Cognito: User sign-up, sign-in, and access control for web and mobile apps.
- Amazon Detective: Investigate security issues.
- AWS Directory Service: Host and manage Active Directory.
- AWS Firewall Manager: **Centrally** configure and manage AWS WAF rules.
- AWS Identity and Access Management (IAM): Securely manage access to AWS services and resources.
- AWS IAM Identity Center (AWS Single Sign-On): Centralized access management for AWS accounts and business applications.
- AWS Key Management Service (AWS KMS): Create and control encryption keys.
- Amazon Macie: Discover, classify, and protect sensitive data using ML.
- AWS Network Firewall: Managed firewall service.
- AWS Resource Access Manager (AWS RAM): Share AWS resources with other accounts.
- AWS Secrets Manager: Store and retrieve secrets.
- AWS Security Hub: Centralized view of security alerts and compliance status.
- AWS Shield: DDoS protection service.
- AWS WAF: Web application firewall service.

Serverless:

- AWS Fargate: Serverless compute engine for containers.
- AWS Lambda: Run code without provisioning or managing servers.

Storage:

- AWS Backup: Centralized backup service.
- AWS Elastic Disaster Recovery: Disaster recovery for on-premises applications.
- Amazon FSx: Fully managed file systems for Windows and Luster.
- AWS Storage Gateway: Hybrid storage service.

Resources:

[https://github.com/kananinirav/AWS-Certified-Cloud-Practitioner-Notes/blob/master/practice-exam/](https://github.com/kananinirav/AWS-Certified-Cloud-Practitioner-Notes/blob/master/practice-exam/)
