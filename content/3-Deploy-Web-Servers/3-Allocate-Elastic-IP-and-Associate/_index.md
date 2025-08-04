---
title : "Allocate Elastic IP and Associate"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---

**Objective:** To provision a static public IP address (Elastic IP) that will act as the stable entry point for client requests, and initially associate it with the primary web server.
#### Execution Steps
1. **Access Elastic IPs:** In the EC2 Dashboard, select **Elastic IPs** from the left navigation pane, under "Network & Security".
2. **Allocate Elastic IP address:** Click the **Allocate Elastic IP address** button.
    
    ![image.png](image.png)
    
3. **Confirm allocation:** Click **Allocate**. Record the **Allocation ID** of the newly allocated EIP.
    
    ![image.png](image%201.png)
    
    ![image.png](image%202.png)
    
4. **Associate Elastic IP with primary instance:**
    - Select the newly allocated EIP.
    - Choose **Actions** -> **Associate Elastic IP address**.
    
    ![image.png](image%203.png)
    
    - **Resource type:** Select `Instance`.
    - **Instance:** Select your `Web-Primary` instance (using its Instance ID).
    - **Reassociation:** Check **Allow this Elastic IP address to be reassociated**
    - Click **Associate**.
    
    ![image.png](image%204.png)
    
5. **Confirm and record:** The Elastic IP is now associated with your primary web server. Record the **Elastic IP address** itself. This IP address will be used to test the web service.
    
    ![image.png](image%205.png)