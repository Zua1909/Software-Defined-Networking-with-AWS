---
title : "Tạo và cấu hình Lambda Function"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Tổng quan về phần Tạo và cấu hình Lambda Function

Phần này của bài lab dành riêng cho việc xây dựng **Control Plane** (mặt phẳng điều khiển) của giải pháp Software-Defined Networking (SDN). Bạn sẽ tạo và cấu hình một hàm serverless AWS Lambda, đóng vai trò là logic cốt lõi cho chính sách định tuyến động của chúng ta. Hàm này sẽ được trang bị các quyền cần thiết (thông qua một IAM Role) và các biến môi trường (cho EIP và các Instance ID) để tương tác với EC2 API. Vai trò chính của hàm này là quản lý việc liên kết Elastic IP bằng lập trình, đảm bảo rằng khi máy chủ chính gặp sự cố, lưu lượng truy cập sẽ được chuyển hướng một cách liền mạch sang máy chủ dự phòng.

#### Các khái niệm chính

* **AWS Lambda:** Một dịch vụ tính toán serverless, hướng sự kiện, cho phép bạn chạy code cho hầu hết mọi loại ứng dụng hoặc dịch vụ backend mà không cần cung cấp hoặc quản lý máy chủ. Đây là công cụ lý tưởng để xây dựng mặt phẳng điều khiển của SDN, vì nó có thể được kích hoạt bởi các sự kiện mạng.
* **Serverless Computing:** Một mô hình thực thi điện toán đám mây, trong đó nhà cung cấp đám mây quản lý máy chủ, cho phép các nhà phát triển chỉ tập trung vào code của họ.
* **Programmatic Network Control (Điều khiển mạng bằng lập trình):** Khả năng quản lý và cấu hình các tài nguyên mạng (như EIP và định tuyến) bằng cách sử dụng code và API, thay vì cấu hình thủ công. Đây là một nguyên tắc cốt lõi của SDN.
* **Environment Variables (Biến môi trường):** Các cặp khóa-giá trị mà bạn có thể lưu trữ trong cấu hình của hàm Lambda để truyền các cài đặt một cách động, chẳng hạn như ID tài nguyên, mà không cần thay đổi code.

#### Nội dung:

* [4.1-Create-Lambda-Function](/4-Create-and-configure-Lambda-Function/1-Create-Lambda-Function)
* [4.2-Configure-Lambda-Environment-Variables](/4-Create-and-configure-Lambda-Function/2-Configure-Lambda-Environment-Variables)
* [4.3-Upload-Lambda-Code](/4-Create-and-configure-Lambda-Function/3-Upload-Lambda-Code)