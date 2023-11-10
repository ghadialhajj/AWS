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
