---
title : "Preparation"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Overview of the Preparation Section

This part of the lab focuses on setting up the foundational AWS infrastructure required for the Software-Defined Networking (SDN) project. You will deploy and configure the core networking components that will form the **Data Plane** of our SDN architecture. This includes creating a secure and isolated network environment (VPC), defining network segments (Subnets), and establishing connectivity (Internet Gateway, Route Tables) and security rules (Security Groups). Additionally, you will create the necessary **IAM Policies and Roles** to grant programmatic permissions to our future control plane component, the AWS Lambda function.

#### Key Concepts

* **Amazon VPC (Virtual Private Cloud):** A logically isolated virtual network where you can launch AWS resources.
* **Subnet:** A range of IP addresses in your VPC. Resources in a public subnet can communicate with the internet, while those in a private subnet cannot.
* **Internet Gateway (IGW):** A horizontally scaled, redundant, and highly available VPC component that allows communication between your VPC and the internet.
* **Route Table:** A set of rules, called routes, that determines where network traffic from your subnets is directed.
* **Security Group:** A virtual firewall that controls inbound and outbound traffic for EC2 instances.
* **IAM (Identity and Access Management):** A service that enables you to manage access to AWS services and resources securely. IAM Policies define permissions, and IAM Roles grant those permissions to AWS services or users.

#### Contents:

* [2.1-Create-VPC](/2-Preparation/1-Create-VPC)
* [2.2-Create-Subnets](/2-Preparation/2-Create-Subnets)
* [2.3-Create-Internet-Gateway](/2-Preparation/3-Create-Internet-Gateway)
* [2.4-Create-Route-Table](/2-Preparation/4-Create-Route-Table)
* [2.5-Create-Security-Groups](/2-Preparation/5-Create-Security-Groups)
* [2.6-Create-IAM-Policy-and-IAM-Role](/2-Preparation/6-Create-IAM-Policy-and-IAM-Role)