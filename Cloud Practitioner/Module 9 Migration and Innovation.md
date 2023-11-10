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
