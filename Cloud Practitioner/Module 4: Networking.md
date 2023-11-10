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
