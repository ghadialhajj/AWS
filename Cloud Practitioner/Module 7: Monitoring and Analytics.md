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
