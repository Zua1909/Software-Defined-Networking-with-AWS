---
title : "Create and configure Lambda Function"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Overview of the Lambda Function Section

This part of the lab is dedicated to building the **Control Plane** of our Software-Defined Networking (SDN) solution. You will create and configure a serverless AWS Lambda function that will act as the core logic for our dynamic routing policy. The function will be equipped with the necessary permissions (via an IAM Role) and environment variables (for EIP and instance IDs) to interact with the EC2 API. The primary role of this function is to programmatically manage the association of the Elastic IP, ensuring that in the event of a primary server failure, traffic is seamlessly redirected to the backup server.

#### Key Concepts

* **AWS Lambda:** A serverless, event-driven compute service that lets you run code for virtually any type of application or backend service without provisioning or managing servers. It is the ideal tool for building the control plane of our SDN, as it can be triggered by network events.
* **Serverless Computing:** A cloud computing execution model where the cloud provider manages the server, allowing developers to focus solely on their code.
* **Programmatic Network Control:** The ability to manage and configure network resources (like EIPs and routing) using code and APIs, rather than manual configuration. This is a core principle of SDN.
* **Environment Variables:** Key-value pairs that you can store in your Lambda function's configuration to dynamically pass settings, such as resource IDs, without changing the code itself.

#### Contents:

* [4.1-Create-Lambda-Function](/4-Create-and-configure-Lambda-Function/1-Create-Lambda-Function)
* [4.2-Configure-Lambda-Environment-Variables](/4-Create-and-configure-Lambda-Function/2-Configure-Lambda-Environment-Variables)
* [4.3-Upload-Lambda-Code](/4-Create-and-configure-Lambda-Function/3-Upload-Lambda-Code)