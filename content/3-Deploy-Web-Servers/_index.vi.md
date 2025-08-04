---
title : "Triển khai Web Servers"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Tổng quan về phần Triển khai Web Servers

Phần này của bài lab tập trung vào việc triển khai các thành phần cốt lõi của dịch vụ web, tạo thành **Data Plane** (mặt phẳng dữ liệu) của giải pháp SDN. Bạn sẽ khởi chạy hai EC2 Instance: một đóng vai trò là máy chủ web chính và một làm máy chủ dự phòng. Để cung cấp một điểm truy cập ổn định và nhất quán cho lưu lượng truy cập của client, bạn cũng sẽ cấp phát một Elastic IP (EIP) và liên kết nó với máy chủ chính. EIP này là tài nguyên mà mặt phẳng điều khiển SDN của chúng ta sẽ quản lý bằng lập trình để đạt được định tuyến động và failover.

#### Các khái niệm chính

* **Amazon EC2 (Elastic Compute Cloud):** Một dịch vụ web cung cấp dung lượng tính toán an toàn, có thể thay đổi kích thước trong đám mây. Đây là dịch vụ cốt lõi để chạy các máy chủ ảo, hay còn gọi là instance.
* **EC2 User Data:** Một script mà bạn có thể cung cấp cho một EC2 Instance để thực hiện các tác vụ tự động khi nó khởi động lần đầu, chẳng hạn như cài đặt một máy chủ web hoặc cấu hình phần mềm.
* **Elastic IP (EIP):** Một địa chỉ IPv4 công cộng, tĩnh, được thiết kế cho điện toán đám mây động. Một EIP có thể được liên kết với bất kỳ EC2 Instance nào trong tài khoản của bạn, và mặt phẳng điều khiển của chúng ta sẽ sử dụng khả năng này để chuyển hướng lưu lượng truy cập trong quá trình failover.
* **Failover:** Quá trình chuyển đổi sang một máy chủ, hệ thống hoặc mạng dự phòng khi ứng dụng, máy chủ hoặc hệ thống đang hoạt động bị lỗi hoặc kết thúc bất thường.

#### Nội dung:

* [3.1-Launch-Web-Primary-EC2](/3-Deploy-Web-Servers/1-Launch-Web-Primary-EC2)
* [3.2-Launch-Web-Backup-EC2](/3-Deploy-Web-Servers/2-Launch-Web-Backup-EC2)
* [3.3-Allocate-Elastic-IP-and-Associate](/3-Deploy-Web-Servers/3-Allocate-Elastic-IP-and-Associate)