---
title : "Xác minh Định tuyến động và Tự động hóa chính sách"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Tổng quan về phần Xác minh

Phần này dành riêng cho giai đoạn quan trọng nhất: xác minh chức năng của giải pháp SDN. Bạn sẽ thử nghiệm toàn bộ hệ thống, từ thiết lập ban đầu đến cơ chế failover tự động. Mục tiêu chính là xác nhận rằng chính sách bạn đã tự động hóa—chuyển hướng lưu lượng truy cập khi máy chủ bị lỗi—hoạt động đúng như dự kiến. Đầu tiên, bạn sẽ xác thực rằng dịch vụ web chính đang chạy, sau đó mô phỏng một lỗi bằng cách dừng EC2 instance chính. Cuối cùng, bạn sẽ quan sát và xác nhận rằng Elastic IP đã được liên kết lại thành công với máy chủ dự phòng, chứng minh rằng mặt phẳng điều khiển SDN đã thực thi thành công chính sách của nó.

#### Các khái niệm chính

* **Định tuyến động (Dynamic Routing):** Khả năng của một mạng tự động điều chỉnh các đường dẫn lưu lượng truy cập để phản ứng với những thay đổi trong cấu trúc liên kết hoặc trạng thái mạng, mà không cần can thiệp thủ công.
* **Tự động hóa chính sách (Policy Automation):** Việc sử dụng các script hoặc code để tự động thực thi các chính sách mạng được xác định trước, chẳng hạn như quy tắc failover, chính sách bảo mật hoặc định hình lưu lượng truy cập.
* **Kiểm thử Failover (Failover Testing):** Quá trình cố ý mô phỏng một lỗi hệ thống để xác minh rằng hệ thống dự phòng hoặc sao lưu tiếp quản thành công và không bị mất dữ liệu.

#### Nội dung:

* [6.1-Initial-Verification](/6-Verify-Dynamic-Routing-and-Policy-Automation/1-Initial-Verification)
* [6.2-Simulate-Web-Primary-Failure](/6-Verify-Dynamic-Routing-and-Policy-Automation/2-Simulate-Web-Primary-Failure)
* [6.3-Verify-Failover-and-Dynamic-Routing](/6-Verify-Dynamic-Routing-and-Policy-Automation/3-Verify-Failover-and-Dynamic-Routing)