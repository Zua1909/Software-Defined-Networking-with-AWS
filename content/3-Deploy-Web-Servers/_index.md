---
title : "Deploy Web Servers"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---
#### Overview of the Web Servers Deployment Section

This part of the lab focuses on deploying the core components of our web service that will form the **Data Plane** of our SDN solution. You will launch two EC2 instances: one to act as the primary web server and the other as a backup. To provide a stable and consistent entry point for client traffic, you will also allocate an Elastic IP (EIP) and associate it with the primary server. This EIP is the resource that our SDN control plane will programmatically manage to achieve dynamic routing and failover.

#### Key Concepts

* **Amazon EC2 (Elastic Compute Cloud):** A web service that provides secure, resizable compute capacity in the cloud. It is the core service for running virtual servers, or instances.
* **EC2 User Data:** A script that you can provide to an EC2 instance to perform automated tasks on its first boot, such as installing a web server or configuring software.
* **Elastic IP (EIP):** A static, public IPv4 address designed for dynamic cloud computing. An EIP can be associated with any EC2 instance in your account, and our control plane will use this capability to redirect traffic during a failover.
* **Failover:** The process of switching to a redundant or standby computer server, system, or network upon the failure or abnormal termination of the previously active application, server, or system.

#### Contents:

* [3.1-Launch-Web-Primary-EC2](/3-Deploy-Web-Servers/1-Launch-Web-Primary-EC2)
* [3.2-Launch-Web-Backup-EC2](/3-Deploy-Web-Servers/2-Launch-Web-Backup-EC2)
* [3.3-Allocate-Elastic-IP-and-Associate](/3-Deploy-Web-Servers/3-Allocate-Elastic-IP-and-Associate)