---
title : "Simulate Web Primary Failure"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

**Objective:** To deliberately induce a failure on the `Web-Primary` EC2 instance, thereby triggering the CloudWatch Alarm and subsequently the SDN-driven failover process.
#### Execution Steps
1. **Access EC2 Dashboard:** Navigate to the EC2 service in the AWS Management Console.
2. **Select Primary Instance:** From the "Instances" list, select your `Web-Primary` EC2 instance.
3. **Stop the Instance:**
    - Choose **Instance state**.
    - Select **Stop instance**.
    - Confirm the action when prompted.
    
    ![image.png](image.png)
    
    ![image.png](image%201.png)
    
4. **Monitor Alarm State:** Allow several minutes for CloudWatch to detect the instance state change. Monitor the `Web-Primary-System-Check-Failed` alarm in the CloudWatch Alarms dashboard. The alarm state is expected to transition from `OK` to `INSUFFICIENT_DATA` and then to `ALARM`.
    
    ![image.png](image%202.png)