---
title : "Create CloudWatch Alarm for Web Primary"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

**Objective:** To set up an alarm that monitors the system health check status of the `Web-Primary` EC2 instance and triggers an alert if a failure is detected.
#### Execution Steps
1. **Access AWS Management Console:** Log in to your AWS account.
2. **Navigate to the CloudWatch service:** In the search bar, type "CloudWatch" and select the CloudWatch service.
    
    ![image.png](image.png)
    
3. **Initiate alarm creation:**
    - Select **All alarms** from the left navigation pane.
    - Click the **Create alarm** button.
    
    ![image.png](image%201.png)
    
4. **Select metric:**
    - Click **Select metric**.
    
    ![image.png](image%202.png)
    
    - Select **EC2 Metrics** -> **Per-Instance Metrics**.\
    
    ![image.png](image%203.png)
    
    ![image.png](image%204.png)
    
    - Locate and select the `StatusCheckFailed_System` metric for your `Web-Primary` instance.
    
    ![image.png](image%205.png)
    
5. **Configure metric and conditions:**
    - **Chosen metric:** `StatusCheckFailed_System` (set Statistic to `Average`, Period to `30 seconds`)
    
    ![image.png](image%206.png)
    
    - **Conditions:**
        - **Threshold type:** Select `Static`.
        - **Whenever StatusCheckFailed_System is:** Select `Greater/Equal`.
        - **than:** Enter `1`.
    - **Additional configuration:**
        - **Missing data treatment:** Select **Treat missing data as bad**
    
    ![image.png](image%207.png)
    
6. **Configure actions:**
    - Click **Next**.
    - **Alarm state trigger:** Ensure `In ALARM` is selected.
    - **Select an SNS topic:**
        - Choose **Create new topic**.
        - **Topic name:** Enter `SDN_Failover_Notifications`
        - Add your email address to receive notifications directly.
        - Click **Create topic**
        
        ![image.png](image%208.png)
        
7. **Configure name and description:**
    - Click **Next**.
    
    ![image.png](image%209.png)
    
    - **Alarm name:** Enter `Web-Primary-System-Check-Failed`
    - **Alarm description:**  `Triggers when Web-Primary instance fails system checks.`
    - Click **Next**
    
    ![image.png](image%2010.png)
    
8. **Complete alarm creation:** Click the **Create alarm** button.
    
    ![image.png](image%2011.png)
    
    ![image.png](image%2012.png)
    
9. Check your email and confirm subscription

![image.png](image%2013.png)