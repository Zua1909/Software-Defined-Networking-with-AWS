---
title : "Create IAM Policy and IAM Role"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 2.6 </b> "
---

**Objective:** To define and assign the necessary permissions for AWS Lambda (our control plane) to execute actions such as reading EC2 Instance information, managing Elastic IPs (associating/disassociating), and writing logs to CloudWatch Logs.
#### Execution Steps
1. **Navigate to the IAM service:** In the AWS Console search bar, type "IAM" and select the IAM service.
    
    ![image.png](image.png)
    
2. **Create IAM Policy (Permissions Policy):**
    - In the left navigation pane, select **Policies**.
    - Click the **Create policy** button.
        
        ![image.png](image%201.png)
        
    - Select the **JSON** tab.
    - Remove the default content and paste the following JSON policy:
        
        ```json
        {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Effect": "Allow",
                    "Action": [
                        "ec2:DescribeInstances",
                        "ec2:AssociateAddress",
                        "ec2:DisassociateAddress",
                        "ec2:DescribeAddresses"
                    ],
                    "Resource": "*"
                },
                {
                    "Effect": "Allow",
                    "Action": [
                        "logs:CreateLogGroup",
                        "logs:CreateLogStream",
                        "logs:PutLogEvents"
                    ],
                    "Resource": "arn:aws:logs:*:*:*"
                }
            ]
        }
        ```
        
    
    ![image.png](image%202.png)
    
    - Click **Next**
    
    ![image.png](image%203.png)
    
    - **Name:** `SDNLambdaEIPControlPolicy`
    - **Description:** `Allows Lambda to control EC2 EIP associations and write logs.`
    
    ![image.png](image%204.png)
    
    - Click the **Create policy** button.
    
    ![image.png](image%205.png)
    
3. **Create IAM Role:**
    - In the left navigation pane, select **Roles**.
    - Click the **Create role** button.
    
    ![image.png](image%206.png)
    
    - **Select trusted entity:** Choose **AWS service**.
    - **Use case:** Select **Lambda**.
    - Click **Next**.
    
    ![image.png](image%207.png)
    
    - **Add permissions:** In the search field, type the name of the Policy just created (`SDNLambdaEIPControlPolicy`) and select it.
    - Click **Next**.
    
    ![image.png](image%208.png)
    
    - **Name, review, and create:**
        - **Role name:** `SDNLambdaRole`
        - **Description:** `Role for Lambda function to manage EIP for SDN failover.`
        
        ![image.png](image%209.png)
        
    - Click the **Create role** button.
    
    ![image.png](image%2010.png)
    
4. **Confirm:** The new Policy and Role will appear in their respective lists.