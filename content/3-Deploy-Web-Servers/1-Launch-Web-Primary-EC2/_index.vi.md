---
title : "Khởi chạy Web Primary EC2"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

**Mục tiêu:** Triển khai EC2 Instance sẽ ban đầu đóng vai trò là máy chủ web chính.
#### Các bước thực hiện
1. **Truy cập EC2 Dashboard:** Điều hướng đến dịch vụ EC2 trong AWS Management Console.

    ![image.png](image.png)

2. **Bắt đầu khởi chạy Instance:** Chọn **Instances** từ bảng điều hướng bên trái, sau đó nhấn **Launch instances**.

    ![image.png](image%201.png)

3. **Tên và thẻ (tags):**
    - **Name:** `Web-Primary`
4. **Chọn Amazon Machine Image (AMI):** Chọn "Amazon Linux 2023 AMI"

    ![image.png](image%202.png)

5. **Chọn Instance Type:** Chọn `t2.micro` hoặc `t3.micro` (đủ điều kiện cho AWS Free Tier).

    ![image.png](image%203.png)

6. **Tạo Key Pair**
    - Nhấn **Create new key pair**
    - **Key pair name**: `sdn-key`
    - **Key pair type**: Chọn **RSA**
    - **Private key file format:** Chọn **.pem**
    - Nhấn **Create key pair**

    ![image.png](image%204.png)

    - **Quan trọng**: Tệp này chỉ được tải xuống một lần. Hãy lưu trữ nó ở nơi an toàn.
7. **Cấu hình chi tiết Instance:**
    - **Network:** Chọn `sdn-project-vpc`
    - **Subnet:** Chọn `sdn-public-subnet-1a`
    - **Auto-assign Public IP:** Đảm bảo `Enable` được chọn.
8. **Cấu hình Security Group:**
    - Chọn một Security Group hiện có.
    - Chọn `web-server-sg` đã tạo trước đó.

    ![image.png](image%205.png)

9. **Cấu hình User Data**
    - Mở rộng **Advanced Details** và tìm mục **User data**.

    ![image.png](image%206.png)

    - Dán script sau để cài đặt Nginx cho một máy chủ web đơn giản:

        ```bash
        #!/bin/bash
        sudo dnf update -y
        sudo dnf install nginx -y
        sudo systemctl start nginx
        sudo systemctl enable nginx
        echo "<h1>Hello from Web-Primary!</h1>" | sudo tee /usr/share/nginx/html/index.html
        ```

    ![image.png](image%207.png)

10. **Khởi chạy Instance:** Nhấn **Launch instance**.

    ![image.png](image%208.png)

11. **Xác nhận và ghi lại:** Ghi lại **Instance ID** của `Web-Primary` instance sau khi khởi chạy thành công.

    ![image.png](image%209.png)

    ![image.png](image%2010.png)