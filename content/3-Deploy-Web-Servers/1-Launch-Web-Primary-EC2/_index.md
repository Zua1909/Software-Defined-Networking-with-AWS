---
title : "Launch Web Primary EC2"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

**Objective:** To deploy the EC2 instance that will initially host the primary web service.
#### Execution Steps
1. **Access EC2 Dashboard:** Navigate to the EC2 service in the AWS Management Console.
    
    ![image.png](image.png)
    
2. **Initiate instance launch:** Select **Instances** from the left navigation pane, then click **Launch instances**.
    
    ![image.png](image%201.png)
    
3. **Name and tags:**
    - **Name:** `Web-Primary`
4. **Choose Amazon Machine Image (AMI):** Select "Amazon Linux 2023 AMI"
    
    ![image.png](image%202.png)
    
5. **Select Instance Type:** Choose `t2.micro` or `t3.micro` (eligible for the AWS Free Tier).
    
    ![image.png](image%203.png)
    
6. **Create a Key Pair**
    - Click **Create new key pair**
    - **Key pair name**: `sdn-key`
    - **Key pair type**: Select **RSA**
    - **Private key file format:** Select **.pem**
    - Click **Create key pair**
    
    ![image.png](image%204.png)
    
    - **Important**: This file will be downloaded only once. Store it safely
7. **Configure Instance Details:**
    - **Network:** Select `sdn-project-vpc`
    - **Subnet:** Select `sdn-public-subnet-1a`
    - **Auto-assign Public IP:** Ensure `Enable` is selected
8. **Configure Security Group:**
    - Select an existing security group.
    - Choose the `web-server-sg` created previously.
    
    ![image.png](image%205.png)
    
9. **Configure User Data**
    - Expand **Advanced Details** and locate **User data**.
    
    ![image.png](image%206.png)
    
    - Paste the following script to install Nginx for a simple web server:
        
        ```bash
        #!/bin/bash
        sudo dnf update -y
        sudo dnf install nginx -y
        sudo systemctl start nginx
        sudo systemctl enable nginx
        echo "<h1>Hello from Web-Primary!</h1>" | sudo tee /usr/share/nginx/html/index.html
        ```
        
    
    ![image.png](image%207.png)
    
10. **Launch Instance:** Click **Launch instance**.
    
    ![image.png](image%208.png)
    
11. **Confirm and record:** Record the **Instance ID** of the `Web-Primary` instance upon successful launch.
    
    ![image.png](image%209.png)
    
    ![image.png](image%2010.png)