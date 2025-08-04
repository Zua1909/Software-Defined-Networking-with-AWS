---
title : "Create Subnets"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

**Objective:** To partition the VPC's IP address space into smaller segments (Subnets) for organized resource placement and enhanced traffic control. Two public Subnets will be created in distinct Availability Zones (AZs) to improve high availability.
#### Execution Steps
1. **Navigate to Subnets:** From the VPC Dashboard, select **Subnets** in the left navigation pane.
2. **Initiate Subnet creation:** Click the **Create subnet** button.
    
    ![image.png](image.png)
    
3. **Configure the first Subnet (Public Subnet 1):**
    - **VPC ID:** Select `sdn-project-vpc`
        
        ![image.png](image%201.png)
        
    - **Subnet name:** Type `sdn-public-subnet-1a`
    - **Availability Zone:** Select `us-east-1a`
    - **IPv4 CIDR block:** Type `10.0.1.0/24`
    
    ![image.png](image%202.png)
    
4. **Complete Subnet 1 creation:** Click the **Create subnet** button.
    
    ![image.png](image%203.png)
    
5. **Configure the second Subnet (Public Subnet 2):** Repeat steps 3 and 4 for a second Subnet:
    - **VPC ID:** Select `sdn-project-vpc`
        
        ![image.png](image%204.png)
        
    - **Subnet name:** Type `sdn-public-subnet-1b`
    - **Availability Zone:** Select  `us-east-1b`
    - **IPv4 CIDR block:** Type `10.0.2.0/24`
    
    ![image.png](image%205.png)
    
6. **Complete Subnet 2 creation:** Click the **Create subnet** button.
    
    ![image.png](image%206.png)
    
7. **Enable automatic public IP assignment for Public Subnets:**
    - Select `sdn-public-subnet-1a`.
    - Choose **Actions** -> **Modify auto-assign IP settings**.
        
        ![image.png](image%207.png)
        
    - Select the **Enable auto-assign public IPv4 address** checkbox.
    - Click **Save**.
        
        ![image.png](image%208.png)
        
        ![image.png](image%209.png)
        
    - Perform the same steps for `sdn-public-subnet-1b`
        
        ![image.png](image%2010.png)
        
        ![image.png](image%2011.png)
        
        ![image.png](image%2012.png)
        
8. **Confirm and record:** The two new Subnets will appear in the list. Record the **Subnet IDs** for both Subnets.