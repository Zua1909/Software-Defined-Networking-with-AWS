---
title : "Initial Verification"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---

**Objective:** To verify that the web service is initially accessible via the Elastic IP and is correctly serving content from the primary web server.
#### Execution Steps
1. **Retrieve Elastic IP Address:** Obtain the Elastic IP address recorded during Section 3.3.
    
    ![image.png](image.png)
    
2. **Access Web Service:** Open a web browser.
3. **Navigate to EIP:** Enter the Elastic IP address with port 80 into the browser's address bar and press Enter.
    
    ![image.png](image%201.png)
    
4. **Confirm Primary Server Response:** The browser should display content indicating "Hello from Web-Primary!", confirming the primary server is operational and reachable through the EIP.
    
    ![image.png](image%202.png)