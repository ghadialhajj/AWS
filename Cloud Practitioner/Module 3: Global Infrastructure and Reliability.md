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
