
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
