---
title : "Tạo CloudWatch Alarm và EventBridge Rule"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Tổng quan về phần Tạo CloudWatch Alarm và EventBridge Rule

Phần này của bài lab là bước cuối cùng để kết nối mặt phẳng điều khiển và mặt phẳng dữ liệu của giải pháp SDN. Bạn sẽ thiết lập cơ chế hướng sự kiện (event-driven) để khởi động quá trình failover. Điều này bao gồm việc tạo một **CloudWatch Alarm** để chủ động giám sát tình trạng sức khỏe của máy chủ web chính. Nếu alarm này được kích hoạt (ví dụ: do một lỗi kiểm tra hệ thống), nó sẽ phát ra một sự kiện. Bạn sẽ sau đó sử dụng **Amazon EventBridge** để bắt sự kiện cụ thể này và kích hoạt **hàm AWS Lambda** của chúng ta. Điều này hoàn thành vòng lặp của SDN: một thay đổi trong trạng thái mạng (máy chủ bị lỗi) được phát hiện, điều này kích hoạt logic của mặt phẳng điều khiển (Lambda), sau đó thực thi một thay đổi trong cấu hình mạng (liên kết lại EIP).

#### Các khái niệm chính

* **Amazon CloudWatch:** Một dịch vụ giám sát và quản lý cung cấp dữ liệu và thông tin chi tiết có thể hành động cho các ứng dụng và tài nguyên cơ sở hạ tầng của AWS, hybrid và on-premises. Nó thu thập dữ liệu giám sát và hoạt động dưới dạng logs, metrics và events.
* **CloudWatch Alarm:** Một alarm giám sát một metric duy nhất hoặc kết quả của một biểu thức toán học dựa trên một metric. Alarm sẽ thực hiện một hoặc nhiều hành động dựa trên giá trị của metric so với một ngưỡng trong một số khoảng thời gian.
* **Amazon EventBridge:** Một event bus serverless giúp dễ dàng kết nối các ứng dụng bằng cách sử dụng dữ liệu từ các ứng dụng của riêng bạn, các ứng dụng SaaS đã tích hợp và các dịch vụ AWS. Các EventBridge rules sẽ khớp với các sự kiện đến và định tuyến chúng đến các đích (target) như một hàm Lambda.
* **Event-Driven Architecture (Kiến trúc hướng sự kiện):** Một mẫu thiết kế phần mềm, trong đó các ứng dụng và dịch vụ không phụ thuộc vào nhau giao tiếp thông qua các sự kiện. Trong bài lab này, sự kiện của CloudWatch là yếu tố kích hoạt hàm Lambda của chúng ta.

#### Nội dung:

* [5.1-Create-CloudWatch-Alarm-for-Web-Primary](/5-Create-CloudWatch-Alarm-and-EventBridge-Rule/1-Create-CloudWatch-Alarm-for-Web-Primary)
* [5.2-Create-EventBridge-Rule-to-Trigger-Lambda](/5-Create-CloudWatch-Alarm-and-EventBridge-Rule/2-Create-EventBridge-Rule-to-Trigger-Lambda)