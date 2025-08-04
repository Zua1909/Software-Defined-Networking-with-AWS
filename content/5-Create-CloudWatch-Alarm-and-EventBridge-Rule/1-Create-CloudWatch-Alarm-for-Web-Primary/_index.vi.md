---
title : "Tạo CloudWatch Alarm cho Web Primary"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

**Mục tiêu:** Thiết lập một alarm để giám sát trạng thái kiểm tra sức khỏe hệ thống của EC2 instance `Web-Primary` và kích hoạt cảnh báo nếu phát hiện lỗi.
#### Các bước thực hiện
1. **Truy cập AWS Management Console:** Đăng nhập vào tài khoản AWS của bạn.
2. **Điều hướng đến dịch vụ CloudWatch:** Trong thanh tìm kiếm, gõ "CloudWatch" và chọn dịch vụ CloudWatch.
    
    ![image.png](image.png)
    
3. **Bắt đầu tạo alarm:**
    - Chọn **All alarms** từ bảng điều hướng bên trái.
    - Nhấn nút **Create alarm**.
    
    ![image.png](image%201.png)
    
4. **Chọn metric:**
    - Nhấn **Select metric**.
    
    ![image.png](image%202.png)
    
    - Chọn **EC2 Metrics** -> **Per-Instance Metrics**.
    
    ![image.png](image%203.png)
    
    ![image.png](image%204.png)
    
    - Định vị và chọn metric `StatusCheckFailed_System` cho instance `Web-Primary` của bạn.
    
    ![image.png](image%205.png)
    
5. **Cấu hình metric và điều kiện:**
    - **Metric đã chọn:** `StatusCheckFailed_System` (đặt Statistic là `Average`, Period là `30 seconds`).
    
    ![image.png](image%206.png)
    
    - **Conditions:**
        - **Threshold type:** Chọn `Static`.
        - **Whenever StatusCheckFailed_System is:** Chọn `Greater/Equal`.
        - **than:** Nhập `1`.
    - **Additional configuration:**
        - **Missing data treatment:** Chọn **Treat missing data as bad**.
    
    ![image.png](image%207.png)
    
6. **Cấu hình actions:**
    - Nhấn **Next**.
    - **Alarm state trigger:** Đảm bảo `In ALARM` được chọn.
    - **Select an SNS topic:**
        - Chọn **Create new topic**.
        - **Topic name:** Nhập `SDN_Failover_Notifications`.
        - Thêm địa chỉ email của bạn để nhận thông báo trực tiếp.
        - Nhấn **Create topic**.
        
    ![image.png](image%208.png)
    
7. **Cấu hình tên và mô tả:**
    - Nhấn **Next**.
    
    ![image.png](image%209.png)
    
    - **Alarm name:** Nhập `Web-Primary-System-Check-Failed`.
    - **Alarm description:** `Triggers when Web-Primary instance fails system checks.`
    - Nhấn **Next**.
    
    ![image.png](image%2010.png)
    
8. **Hoàn tất việc tạo alarm:** Nhấn nút **Create alarm**.
    
    ![image.png](image%2011.png)
    
    ![image.png](image%2012.png)
    
9. Kiểm tra email của bạn và xác nhận đăng ký.
    
    ![image.png](image%2013.png)