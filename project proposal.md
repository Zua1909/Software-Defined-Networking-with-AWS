### Project Proposal: Software-Defined Networking with AWS

---

### Tóm tắt (Executive Summary)
Đề xuất này trình bày một giải pháp Software-Defined Networking (SDN) nhằm tự động hóa quá trình failover cho dịch vụ web, đảm bảo tính sẵn sàng cao và khả năng phục hồi của hệ thống. Giải pháp sử dụng các dịch vụ AWS như EC2, Lambda, CloudWatch và EventBridge để tạo ra một mặt phẳng điều khiển (Control Plane) có khả năng lập trình, tự động điều chỉnh các tài nguyên mạng (Data Plane) khi phát hiện lỗi. Giải pháp sẽ tự động chuyển hướng lưu lượng truy cập từ máy chủ web chính bị lỗi sang máy chủ dự phòng thông qua việc liên kết lại Elastic IP. Mục tiêu của dự án là minh họa các nguyên tắc SDN, giảm thiểu thời gian ngừng hoạt động, và cung cấp một mô hình thực tế về cách tự động hóa mạng có thể được áp dụng trong môi trường đám mây.

### 1. Vấn đề (Problem Statement)
Trong các kiến trúc mạng truyền thống, việc chuyển đổi dự phòng (failover) khi một máy chủ gặp sự cố thường đòi hỏi sự can thiệp thủ công hoặc sử dụng các giải pháp phức tạp. Điều này dẫn đến:
* **Thời gian ngừng hoạt động cao:** Việc phát hiện lỗi và chuyển đổi sang máy chủ dự phòng không diễn ra ngay lập tức, làm tăng thời gian ngừng hoạt động của dịch vụ.
* **Chi phí vận hành:** Các kỹ sư phải giám sát thủ công và can thiệp kịp thời, làm tăng chi phí và rủi ro lỗi do con người.
* **Thiếu khả năng mở rộng:** Các quy trình thủ công không phù hợp với các hệ thống có quy mô lớn hoặc thay đổi liên tục.
* **Tính không nhất quán:** Các quy trình failover thủ công có thể không nhất quán, gây ra các sự cố không lường trước được.

Đề xuất này giải quyết những vấn đề trên bằng cách tự động hóa hoàn toàn quy trình failover, loại bỏ sự can thiệp của con người và giảm thiểu thời gian ngừng hoạt động xuống gần như bằng không.

### 2. Kiến trúc giải pháp (Solution Architecture)
Kiến trúc giải pháp được thiết kế để tách biệt mặt phẳng điều khiển và mặt phẳng dữ liệu, một nguyên tắc cốt lõi của SDN.

* **Sơ đồ kiến trúc:**
  * **Data Plane:** Gồm một VPC với hai public subnet riêng biệt. Mỗi subnet chứa một EC2 instance (`Web-Primary` và `Web-Backup`). Một Internet Gateway cung cấp kết nối Internet cho VPC, và một Elastic IP duy nhất đóng vai trò là điểm truy cập công cộng cho dịch vụ.
  * **Control Plane:** Gồm ba dịch vụ AWS hoạt động ở cấp độ Region.
    * **CloudWatch Alarm:** Giám sát metric `StatusCheckFailed_System` của `Web-Primary` instance.
    * **EventBridge Rule:** Lắng nghe sự kiện từ CloudWatch và kích hoạt hàm Lambda khi trạng thái Alarm chuyển sang `ALARM`.
    * **Lambda Function:** Thực thi logic failover bằng cách gọi EC2 API để hủy liên kết EIP khỏi `Web-Primary` và liên kết nó với `Web-Backup`.

* **Các dịch vụ AWS được sử dụng:**
  * **EC2:** Nền tảng máy chủ ảo để chạy web service.
  * **VPC:** Môi trường mạng ảo.
  * **Elastic IP:** Địa chỉ IP công cộng tĩnh cho dịch vụ.
  * **CloudWatch:** Dịch vụ giám sát.
  * **EventBridge:** Dịch vụ bus sự kiện để tự động hóa.
  * **Lambda:** Dịch vụ tính toán serverless cho logic điều khiển.
  * **IAM:** Quản lý quyền hạn cho các dịch vụ.

* **Tính bảo mật:** Security Group sẽ được cấu hình để chỉ cho phép lưu lượng truy cập HTTP, HTTPS và SSH từ các nguồn đáng tin cậy. IAM Role sẽ tuân thủ nguyên tắc quyền tối thiểu (Least Privilege), chỉ cấp cho Lambda các quyền cần thiết để quản lý EIP.

### 3. Kế hoạch triển khai kỹ thuật (Technical Implementation)
Quá trình triển khai sẽ được chia thành các giai đoạn rõ ràng:
1.  **Chuẩn bị (Preparation):** Triển khai cơ sở hạ tầng mạng cơ bản (VPC, Subnets, IGW, Route Tables, Security Group) và IAM Role cần thiết.
2.  **Triển khai Web Servers:** Khởi chạy hai EC2 Instance (`Web-Primary` và `Web-Backup`) và cấu hình User Data để tự động cài đặt Nginx. Cấp phát và liên kết Elastic IP với `Web-Primary`.
3.  **Xây dựng Control Plane:** Viết và triển khai hàm Lambda với logic failover, sử dụng các biến môi trường để lưu trữ ID của các tài nguyên.
4.  **Thiết lập Tự động hóa:** Tạo CloudWatch Alarm để giám sát `Web-Primary` và một EventBridge Rule để kích hoạt Lambda khi có lỗi.
5.  **Xác minh và kiểm thử:** Mô phỏng lỗi máy chủ chính và xác minh rằng quá trình failover diễn ra tự động và thành công.

### 4. Thời gian và các mốc quan trọng (Timeline & Milestones)
* **Giai đoạn 1 (Tuần 1-2): Thiết kế và Chuẩn bị.**
  * Thiết kế kiến trúc và viết proposal.
  * Triển khai VPC, Subnets, IGW, Route Tables và IAM Role.
* **Giai đoạn 2 (Tuần 3): Triển khai & Lập trình.**
  * Khởi chạy EC2 Instances và cấu hình User Data.
  * Phát triển và triển khai hàm Lambda.
* **Giai đoạn 3 (Tuần 4): Tự động hóa & Kiểm thử.**
  * Cấu hình CloudWatch Alarm và EventBridge Rule.
  * Thực hiện kiểm thử failover và xác minh kết quả.

### 5. Ước tính chi phí (Budget Estimation)
Giải pháp này sử dụng các dịch vụ AWS theo mô hình pay-as-you-go.
* **EC2:** Chi phí sẽ dựa trên hai instance `t2.micro` hoặc `t3.micro`. Đây là các instance thuộc Free Tier, do đó chi phí có thể rất thấp.
* **Elastic IP:** Có một khoản phí nhỏ nếu EIP không được liên kết với một instance đang chạy.
* **Lambda:** Chi phí dựa trên số lần thực thi và thời gian chạy. Trong kịch bản này, chi phí sẽ rất nhỏ vì hàm chỉ chạy khi có sự cố.
* **CloudWatch và EventBridge:** Có một số lượng yêu cầu miễn phí hàng tháng.

Với quy mô của bài lab, chi phí ước tính sẽ nằm trong giới hạn của AWS Free Tier, do đó chi phí tổng thể sẽ rất thấp, phù hợp với một dự án sinh viên.

### 6. Đánh giá rủi ro (Risk Assessment)
* **Rủi ro kỹ thuật:**
  * **Lỗi cấu hình:** Các lỗi trong User Data, Security Group hoặc IAM Policy có thể làm hệ thống không hoạt động.
  * **Chiến lược giảm thiểu:** Thực hiện kiểm tra từng bước, sử dụng Infrastructure as Code (IaC) để đảm bảo tính nhất quán và kiểm tra nhật ký CloudWatch để tìm lỗi.
* **Rủi ro vận hành:**
  * **Lỗi trong code Lambda:** Lỗi cú pháp hoặc logic trong hàm Lambda có thể khiến quá trình failover thất bại.
  * **Chiến lược giảm thiểu:** Sử dụng các bài kiểm thử Lambda và kiểm tra nhật ký chi tiết để nhanh chóng phát hiện và sửa lỗi.

### 7. Kết quả mong đợi (Expected Outcomes)
* **Kết quả kỹ thuật:** Xây dựng thành công một kiến trúc SDN hoạt động trên AWS, với cơ chế failover tự động và thời gian ngừng hoạt động tối thiểu.
* **Kết quả học tập:** Hiểu rõ các nguyên tắc của SDN, cách hoạt động của mặt phẳng điều khiển và dữ liệu, và cách tích hợp các dịch vụ AWS để tạo ra các giải pháp tự động hóa mạng.
* **Giá trị dài hạn:** Xây dựng một mô hình failover tự động có thể mở rộng và áp dụng cho các ứng dụng thực tế, thể hiện khả năng thiết kế và triển khai các giải pháp đám mây chuyên nghiệp.