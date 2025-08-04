---
title : "Preparation"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Tổng quan về phần Chuẩn bị

Phần này của bài lab tập trung vào việc thiết lập cơ sở hạ tầng AWS nền tảng cần thiết cho dự án Software-Defined Networking (SDN). Bạn sẽ triển khai và cấu hình các thành phần mạng cốt lõi tạo thành **Data Plane** (mặt phẳng dữ liệu) của kiến trúc SDN. Điều này bao gồm việc tạo một môi trường mạng an toàn và cô lập (VPC), định nghĩa các phân đoạn mạng (Subnets), thiết lập kết nối (Internet Gateway, Route Tables) và các quy tắc bảo mật (Security Groups). Ngoài ra, bạn cũng sẽ tạo các **IAM Policies và Roles** cần thiết để cấp quyền truy cập lập trình cho thành phần điều khiển (control plane) trong tương lai, là hàm AWS Lambda.

#### Các khái niệm chính

* **Amazon VPC (Virtual Private Cloud):** Một mạng ảo được cô lập về mặt logic, nơi bạn có thể khởi chạy các tài nguyên AWS.
* **Subnet:** Một dải địa chỉ IP trong VPC của bạn. Các tài nguyên trong Public Subnet có thể giao tiếp với Internet, trong khi các tài nguyên trong Private Subnet thì không.
* **Internet Gateway (IGW):** Một thành phần VPC được mở rộng theo chiều ngang, dự phòng và có tính sẵn sàng cao, cho phép giao tiếp giữa VPC của bạn và Internet.
* **Route Table:** Một tập hợp các quy tắc, gọi là các tuyến (routes), xác định nơi lưu lượng mạng từ các Subnet của bạn được định hướng.
* **Security Group:** Một tường lửa ảo kiểm soát lưu lượng ra và vào cho các EC2 Instance.
* **IAM (Identity and Access Management):** Một dịch vụ cho phép bạn quản lý quyền truy cập vào các dịch vụ và tài nguyên AWS một cách an toàn. IAM Policies định nghĩa các quyền hạn, và IAM Roles cấp các quyền đó cho các dịch vụ hoặc người dùng AWS.

#### Nội dung:

* [2.1-Create-VPC](/2-Preparation/1-Create-VPC)
* [2.2-Create-Subnets](/2-Preparation/2-Create-Subnets)
* [2.3-Create-Internet-Gateway](/2-Preparation/3-Create-Internet-Gateway)
* [2.4-Create-Route-Table](/2-Preparation/4-Create-Route-Table)
* [2.5-Create-Security-Groups](/2-Preparation/5-Create-Security-Groups)
* [2.6-Create-IAM-Policy-and-IAM-Role](/2-Preparation/6-Create-IAM-Policy-and-IAM-Role)