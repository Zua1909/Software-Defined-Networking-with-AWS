---
title : "Tạo Internet Gateway"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

**Mục tiêu:** Cho phép các tài nguyên trong Public Subnet của VPC giao tiếp với Internet.
#### Các bước thực hiện
1. **Điều hướng đến Internet Gateways:** Trong VPC Dashboard, chọn **Internet Gateways** từ bảng điều hướng bên trái.
2. **Bắt đầu tạo Internet Gateway:** Nhấn nút **Create internet gateway**.

    ![image.png](image.png)

3. **Cấu hình Internet Gateway:**
    - **Name tag:** Nhập `sdn-project-igw`
4. **Hoàn tất tạo Internet Gateway:** Nhấn nút **Create internet gateway**.

    ![image.png](image%201.png)

5. **Gắn Internet Gateway vào VPC:**
    - Sau khi IGW được tạo (nó sẽ ở trạng thái `Detached`), chọn IGW vừa tạo.
    - Chọn **Actions** -> **Attach to VPC**.

    ![image.png](image%202.png)

    - Chọn `sdn-project-vpc` từ danh sách thả xuống.
    - Nhấn nút **Attach internet gateway**.

    ![image.png](image%203.png)

6. **Xác nhận việc gắn vào:** **State** của Internet Gateway sẽ chuyển thành `Attached`.

    ![image.png](image%204.png)