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
