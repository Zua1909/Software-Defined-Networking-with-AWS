---
title : "Create CloudWatch Alarm and EventBridge Rule"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Overview of the CloudWatch Alarm and EventBridge Rule Section

This part of the lab is the final step in connecting our SDN control and data planes. You will establish the event-driven mechanism that initiates the failover process. This involves creating a **CloudWatch Alarm** to actively monitor the health of the primary web server. If this alarm is triggered (e.g., due to a system check failure), it will emit an event. You will then use **Amazon EventBridge** to capture this specific event and, in turn, trigger our **AWS Lambda function**. This completes the SDN loop: a change in the network state (server failure) is detected, which triggers our control plane logic (Lambda), which then executes a change in the network configuration (EIP re-association).

#### Key Concepts

* **Amazon CloudWatch:** A monitoring and management service that provides data and actionable insights for AWS, hybrid, and on-premises applications and infrastructure resources. It collects monitoring and operational data in the form of logs, metrics, and events.
* **CloudWatch Alarm:** An alarm that watches a single metric or the result of a math expression based on a metric. The alarm performs one or more actions based on the value of the metric relative to a threshold over a number of time periods.
* **Amazon EventBridge:** A serverless event bus that makes it easy to connect applications using data from your own applications, integrated Software-as-a-Service (SaaS) applications, and AWS services. EventBridge rules match incoming events and route them to targets like a Lambda function.
* **Event-Driven Architecture:** A software design pattern where decoupled applications and services communicate through events. In this lab, the CloudWatch event is the trigger for our Lambda function.

#### Contents:

* [5.1-Create-CloudWatch-Alarm-for-Web-Primary](/5-Create-CloudWatch-Alarm-and-EventBridge-Rule/1-Create-CloudWatch-Alarm-for-Web-Primary)
* [5.2-Create-EventBridge-Rule-to-Trigger-Lambda](/5-Create-CloudWatch-Alarm-and-EventBridge-Rule/2-Create-EventBridge-Rule-to-Trigger-Lambda)