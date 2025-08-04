---
title : "Xác minh Failover và Định tuyến động"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 6.3 </b> "
---

**Mục tiêu:** Xác nhận rằng Elastic IP đã được hủy liên kết thành công khỏi máy chủ chính bị lỗi và được liên kết lại với máy chủ dự phòng, cho thấy định tuyến động và tự động hóa chính sách đã thành công.
#### Các bước thực hiện
1. **Xác minh Liên kết Elastic IP:**
    - Điều hướng trở lại dịch vụ EC2.
    - Chọn **Elastic IPs** từ bảng điều hướng bên trái.
    - Kiểm tra chi tiết của Elastic IP của bạn. Xác nhận rằng liên kết của nó đã thay đổi và nó hiện được liên kết với EC2 instance `Web-Backup`.
    
    ![image.png](image.png)
    
2. **Truy cập dịch vụ Web qua EIP (Lần thử thứ hai)**
    - Tải lại trình duyệt web của bạn.
    - **Xác nhận Phản hồi từ máy chủ dự phòng:** Trình duyệt bây giờ sẽ hiển thị nội dung "Hello from Web-Backup!". Điều này chứng minh rằng lưu lượng truy cập đã được chuyển hướng động đến máy chủ dự phòng khỏe mạnh bởi mặt phẳng điều khiển SDN.
    
    ![image.png](image%201.png)