---
title : "Dọn dẹp tài nguyên"
date : "`r Sys.Date()`"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

Phần cuối cùng này cung cấp hướng dẫn toàn diện để xóa một cách có hệ thống tất cả các tài nguyên AWS đã được triển khai trong bài lab. Tuân thủ các bước này là rất quan trọng để tránh phát sinh các chi phí không cần thiết trong tài khoản AWS của bạn.

#### Chấm dứt EC2 Instances

- **Mục tiêu:** Chấm dứt cả EC2 instance chính và dự phòng, đảm bảo chúng không còn tiêu tốn tài nguyên tính toán.
- **Các bước thực hiện:**
    1. **Truy cập EC2 Dashboard:** Điều hướng đến dịch vụ EC2 trong AWS Management Console.
    2. **Chọn Instances:** Từ danh sách "Instances", chọn cả hai EC2 instance `Web-Primary` và `Web-Backup` của bạn.
    3. **Chấm dứt Instances:**
        - Chọn **Instance state**.
        - Chọn **Terminate instance**.
        - Xác nhận hành động khi được hỏi.

        ![image.png](image.png)

        ![image.png](image%201.png)


#### Giải phóng Elastic IP

- **Mục tiêu:** Hủy liên kết (nếu vẫn còn) và giải phóng địa chỉ Elastic IP, làm cho nó khả dụng cho các tài khoản AWS khác và chấm dứt mọi khoản phí tiềm năng.
- **Các bước thực hiện:**
    1. **Truy cập Elastic IPs:** Trong EC2 Dashboard, chọn **Elastic IPs** từ bảng điều hướng bên trái.
    2. **Hủy liên kết EIP (nếu cần):** Nếu EIP vẫn còn được liên kết với bất kỳ instance nào, chọn EIP đó, chọn **Actions**, và sau đó chọn **Disassociate Elastic IP address**. Xác nhận hành động.

        ![image.png](image%202.png)

        ![image.png](image%203.png)

    3. **Giải phóng EIP:** Chọn EIP. Chọn **Actions**, và sau đó chọn **Release Elastic IP address**. Xác nhận hành động.

    ![image.png](image%204.png)

    ![image.png](image%205.png)


#### Xóa Lambda Function

- **Mục tiêu:** Xóa hàm AWS Lambda, vốn là mặt phẳng điều khiển SDN, đảm bảo code và cấu hình của nó bị xóa.
- **Các bước thực hiện:**
    1. **Truy cập Lambda Service:** Điều hướng đến dịch vụ Lambda trong AWS Management Console.
    2. **Chọn Lambda Function:** Chọn `SDNEIPFailoverFunction` của bạn.
    3. **Xóa Function:** Chọn **Actions**, và sau đó chọn **Delete function**. Xác nhận việc xóa.

    ![image.png](image%206.png)

    ![image.png](image%207.png)


#### Xóa CloudWatch Alarm

- **Mục tiêu:** Xóa alarm CloudWatch đã được cấu hình để giám sát sức khỏe của máy chủ web chính.
- **Các bước thực hiện:**
    1. **Truy cập CloudWatch Service:** Điều hướng đến dịch vụ CloudWatch.
    2. **Chọn Alarms:** Chọn **Alarms** từ bảng điều hướng bên trái.
    3. **Xóa Alarm:** Chọn alarm `Web-Primary-System-Check-Failed`. Chọn **Actions**, và sau đó chọn **Delete**. Xác nhận việc xóa.

    ![image.png](image%208.png)

    ![image.png](image%209.png)


#### Xóa EventBridge Rule

- **Mục tiêu:** Xóa EventBridge rule đã liên kết alarm CloudWatch với hàm Lambda.
- **Các bước thực hiện:**
    1. **Truy cập EventBridge Service:** Điều hướng đến dịch vụ EventBridge.
    2. **Chọn Rules:** Chọn **Rules** từ bảng điều hướng bên trái.
    3. **Xóa Rule:** Chọn `SDN-Failover-Rule` của bạn. Chọn **Actions**, và sau đó chọn **Delete**. Xác nhận việc xóa.

    ![image.png](image%2010.png)

    ![image.png](image%2011.png)


#### Xóa IAM Role và Policy

- **Mục tiêu:** Xóa IAM role và policy đã cấp quyền cho hàm Lambda, đảm bảo tất cả các quyền truy cập liên quan đều bị thu hồi.
- **Các bước thực hiện:**
    1. **Truy cập IAM Service:** Điều hướng đến dịch vụ IAM.
    2. **Xóa IAM Role:**
        - Chọn **Roles** từ bảng điều hướng bên trái.
        - Chọn `SDNLambdaRole`. Chọn **Delete role**. Xác nhận việc xóa.

        ![image.png](image%2012.png)

        ![image.png](image%2013.png)

    3. **Xóa IAM Policy:**
        - Chọn **Policies** từ bảng điều hướng bên trái.
        - Chọn `SDNLambdaEIPControlPolicy`. Chọn **Actions**, và sau đó chọn **Delete**. Xác nhận việc xóa.

        ![image.png](image%2014.png)

        ![image.png](image%2015.png)


#### Xóa VPC

- **Mục tiêu:** Xóa Virtual Private Cloud, vốn là môi trường mạng nền tảng cho bài lab này. Đây là bước cuối cùng trong việc dọn dẹp tài nguyên.
- **Các bước thực hiện:**
    1. **Truy cập Your VPCs:** Điều hướng đến dịch vụ VPC, sau đó chọn **Your VPCs**.
    2. **Xóa VPC:** Chọn `sdn-project-vpc`. Chọn **Actions**, và sau đó chọn **Delete VPC**. Xác nhận việc xóa. *Lưu ý: Đảm bảo tất cả các tài nguyên liên quan (instances, EIPs, IGWs, subnets, v.v.) đã được xóa hoặc hủy liên kết trước khi cố gắng xóa VPC. AWS sẽ ngăn chặn việc xóa VPC nếu các tài nguyên đang hoạt động vẫn còn bên trong.*

    ![image.png](image%2016.png)

    ![image.png](image%2017.png)