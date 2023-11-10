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
