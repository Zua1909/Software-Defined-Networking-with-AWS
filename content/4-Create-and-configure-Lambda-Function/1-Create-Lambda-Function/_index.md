---
title : "Create Lambda Function"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

**Objective:** To create the AWS Lambda function that will execute the SDN logic, specifically managing the EIP failover.
#### Execution Steps
1. **Access AWS Management Console:** Log in to your AWS account.
2. **Navigate to the Lambda service:** In the search bar, type "Lambda" and select the Lambda service.
    
    ![image.png](image.png)
    
3. **Initiate function creation:**
    - Select **Functions** from the left navigation pane.
    - Click the **Create function** button.
    
    ![image.png](image%201.png)
    
4. **Configure basic function settings:**
    - **Author from scratch:** Select this option.
    - **Function name:**  `SDNEIPFailoverFunction`
    - **Runtime:** Select `Python 3.9`
    - **Architecture:** Select `x86_64`
    
    ![image.png](image%202.png)
    
    - **Permissions:** Under "Change default execution role", select **Use an existing role**. Choose the `SDNLambdaRole` previously created from the dropdown list.
    
    ![image.png](image%203.png)
    
5. **Complete function creation:** Click the **Create function** button.