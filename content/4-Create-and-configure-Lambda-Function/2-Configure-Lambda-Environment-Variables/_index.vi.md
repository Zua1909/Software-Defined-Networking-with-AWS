---
title : "Cấu hình Biến Môi trường Lambda"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

**Mục tiêu:** Cung cấp cho hàm Lambda những thông tin cần thiết, bao gồm Allocation ID của Elastic IP và Instance ID của cả máy chủ web chính và máy chủ dự phòng, để nó có thể thực hiện các thao tác failover.
#### Các bước thực hiện
1. **Truy cập cấu hình hàm Lambda:** Sau khi `SDNEIPFailoverFunction` được tạo, chọn tab **Configuration**.
2. **Chỉnh sửa biến môi trường:**
    - Chọn **Environment variables** từ menu bên trái.
    - Nhấn nút **Edit**.
    
    ![image.png](image.png)
    
3. **Thêm các biến bắt buộc:**
    - Nhấn **Add environment variable**.
        - **Key:** `EIP_ALLOCATION_ID`
        - **Value:** Nhập **Allocation ID** của Elastic IP đã ghi lại trong Phần 3.3.
    - Nhấn **Add environment variable**.
        - **Key:** `WEB_BACKUP_INSTANCE_ID`
        - **Value:** Nhập **Instance ID** của EC2 instance `Web-Backup` đã ghi lại trong Phần 3.2.
    - Nhấn **Add environment variable**.
        - **Key:** `WEB_PRIMARY_INSTANCE_ID`
        - **Value:** Nhập **Instance ID** của EC2 instance `Web-Primary` đã ghi lại trong Phần 3.1.
4. **Lưu thay đổi:** Nhấn nút **Save**.
    
    ![image.png](image%201.png)