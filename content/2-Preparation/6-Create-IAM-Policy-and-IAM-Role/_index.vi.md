---
title : "Tạo IAM Policy và IAM Role"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 2.6 </b> "
---

**Mục tiêu:** Định nghĩa và gán các quyền cần thiết cho AWS Lambda (mặt phẳng điều khiển của chúng ta) để thực hiện các hành động như đọc thông tin EC2 Instance, quản lý Elastic IP (liên kết/hủy liên kết), và ghi nhật ký vào CloudWatch Logs.
#### Các bước thực hiện
1. **Điều hướng đến dịch vụ IAM:** Trong thanh tìm kiếm của AWS Console, gõ "IAM" và chọn dịch vụ IAM.
    
    ![image.png](image.png)
    
2. **Tạo IAM Policy (Chính sách quyền hạn):**
    - Trong bảng điều hướng bên trái, chọn **Policies**.
    - Nhấn nút **Create policy**.
        
        ![image.png](image%201.png)
        
    - Chọn tab **JSON**.
    - Xóa nội dung mặc định và dán đoạn JSON policy sau:
        
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
    
    - Nhấn **Next**
    
    ![image.png](image%203.png)
    
    - **Name:** `SDNLambdaEIPControlPolicy`
    - **Description:** `Allows Lambda to control EC2 EIP associations and write logs.`
    
    ![image.png](image%204.png)
    
    - Nhấn nút **Create policy**.
    
    ![image.png](image%205.png)
    
3. **Tạo IAM Role:**
    - Trong bảng điều hướng bên trái, chọn **Roles**.
    - Nhấn nút **Create role**.
    
    ![image.png](image%206.png)
    
    - **Select trusted entity:** Chọn **AWS service**.
    - **Use case:** Chọn **Lambda**.
    - Nhấn **Next**.
    
    ![image.png](image%207.png)
    
    - **Add permissions:** Trong trường tìm kiếm, gõ tên Policy vừa tạo (`SDNLambdaEIPControlPolicy`) và chọn nó.
    - Nhấn **Next**.
    
    ![image.png](image%208.png)
    
    - **Name, review, and create:**
        - **Role name:** `SDNLambdaRole`
        - **Description:** `Role for Lambda function to manage EIP for SDN failover.`
        
        ![image.png](image%209.png)
        
    - Nhấn nút **Create role**.
    
    ![image.png](image%2010.png)
    
4. **Xác nhận:** Policy và Role mới sẽ xuất hiện trong danh sách tương ứng.