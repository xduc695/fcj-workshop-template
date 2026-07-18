---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
### Mục tiêu tuần 2:

* Tìm hiểu sâu hơn về các dịch vụ mạng trên AWS.
* Làm quen cách tự thiết kế, khởi tạo một hệ thống mạng ảo (VPC) và thiết lập các kết nối an toàn (VPN) để kết nối dữ liệu.
* Học cách sử dụng Session Manager và triển khai truy cập trực tiếp vào máy chủ EC2 trong VPC thay thế cho SSH.
* Học cách sử dụng VPC Peering để kết nối hai VPC khác nhau, cho phép các máy chủ giao tiếp trực tiếp bằng IP nội bộ thay vì đi qua Internet.
* Học cách sử dụng Transit Gateway làm hub trung tâm và triển khai kết nối nhiều VPC thông qua một bộ định tuyến tập trung để đơn giản hóa kiến trúc mạng thay thế cho cách kết nối VPC Peering phức tạp.
* Học cách xây dựng hệ thống DNS hybrid và triển khai tích hợp hệ thống DNS on-premise với Amazon Route 53 thông qua Inbound/Outbound Endpoints và Resolver Rules.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Tìm hiểu sâu hơn về các dịch vụ mạng trên AWS: <br>&emsp; + Amazon Virtual Private Cloud (VPC) <br>&emsp; + VPC Peering & Transit Gateway <br>&emsp; + VPN & Direct connect <br>&emsp; + Elastic Load Balancing | 27/04/2026 | 27/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thứ 3 | - Làm quen với Amazon VPC và các thành phần cơ bản: Subnets, Route Table, Internet Gateway, NAT Gateway.<br> - Làm quen với tường lửa trong VPC: Security Groups, Network ACLs.<br> - Tìm hiểu thêm về VPC Resource Map.<br> - **Thực hành:**<br>&emsp; + Khởi tạo VPC, Subnet, IGW, Route Table, Security Group.<br>&emsp; + Kích hoạt VPC Flow Logs.<br> - Tiến hành triển khai Hạ tầng EC2 Production-Ready.<br> - **Thực hành:**<br>&emsp; + Triển khai EC2 Instances và kiểm tra kết nối SSH.<br>&emsp; + Khởi tạo NAT Gateway.<br>&emsp; + Sử dụng Reachability Analyzer.<br>&emsp; + Khởi tạo và kết nối qua EC2 Instance Connect Endpoint.<br>&emsp; + Triển khai CloudWatch Monitoring & Alerting. | 28/04/2026 | 28/04/2026 | <https://000003.awsstudygroup.com/> |
| Thứ 4 | - Triển khai thiết lập môi trường AWS Site-to-Site VPN.<br> - **Thực hành:** <br>&emsp; + Thiết lập VPC cho VPN, EC2 Customer Gateway.<br>&emsp; + Khởi tạo Virtual Private Gateway và Customer Gateway.<br>&emsp; + Thiết lập AWS Site-to-Site VPN Connection.<br>&emsp; + Tùy chỉnh AWS VPN Tunnel.<br> - Tìm hiểu cấu hình VPN bảo mật cao, Troubleshooting VPN.<br> - Mở rộng kết nối VPN bằng strongSwan với Transit Gateway.<br> - Tìm hiểu Infrastructure as Code (CloudFormation). | 29/04/2026 | 29/04/2026 | <https://000003.awsstudygroup.com/> |
| Thứ 5 | - Tìm hiểu Amazon System Manager - Session Manager.<br>- **Thực hành:** <br>&emsp; + Khởi tạo VPC, Subnets, Security Groups.<br>&emsp; + Tạo Public Linux EC2 và Private Windows EC2.<br>&emsp; + Tạo IAM Role cho EC2 giao tiếp với Session Manager.<br>&emsp; + Tạo SSM Endpoints và kết nối máy chủ Private Windows.<br>&emsp; + Cập nhật IAM Role cho EC2 truy cập S3.<br>&emsp; + Khởi tạo S3 bucket lưu session logs.<br>&emsp; + Cấu hình Port Forwarding cho RDP.<br> - Thiết lập Hybrid DNS với Route 53 Resolver.<br> - **Thực hành:** <br>&emsp; + Tạo AWS Managed Microsoft AD (giả lập DNS On-premises).<br>&emsp; + Cấu hình Route 53 Outbound Endpoint và Resolver Rules.<br>&emsp; + Cấu hình Route 53 Inbound Endpoint.<br>&emsp; + Phân giải tên miền chéo. | 30/04/2026 | 30/04/2026 | <https://000058.awsstudygroup.com/> <br><https://000010.awsstudygroup.com/>|
| Thứ 6 | - Thiết lập VPC Peering.<br> - **Thực hành:** <br>&emsp; + Tạo nhanh 2 VPC qua CloudFormation.<br>&emsp; + Tạo VPC Peering Connection, cập nhật Route Table.<br>&emsp; + Kích hoạt DNS Resolution Support (Cross-Peer DNS).<br> - Triển khai Transit Gateway với 4 VPC.<br> - **Thực hành:**<br>&emsp; + Dùng CloudFormation triển khai nhanh 4 VPC.<br>&emsp; + Tạo Transit Gateway và Transit Gateway Attachments.<br>&emsp; + Cấu hình Route Table cho Transit Gateway và từng VPC.<br>&emsp; + Kiểm tra kết nối liên mạng. | 01/05/2026 | 01/05/2026 | <https://000019.awsstudygroup.com/><br><https://000020.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

* Làm chủ kiến thức về Amazon VPC:
  * Phân biệt và thiết lập thành công Subnets (Public/Private), Route Table và cổng Gateway (Internet/NAT).
  * Thấu hiểu hàng rào bảo mật 2 lớp: Security Group (lọc máy chủ) và Network ACL (lọc tầng mạng).
  * Sử dụng VPC Resource Map để quản trị trực quan toàn bộ sơ đồ tài nguyên mạng.

* Mở rộng và Kết nối liên thông:
  * VPC Peering: Thiết lập kết nối ngang hàng trực tiếp giữa các VPC khác nhau.
  * Transit Gateway: Làm chủ mô hình định tuyến tập trung (Hub-and-Spoke) cho hệ thống quy mô lớn.

* Hiểu rõ Hybrid Cloud & High Availability:
  * VPN: Nắm vững cách tạo kênh truyền mã hóa Site-to-Site để kết nối an toàn với On-premises.
  * Direct Connect: Hiểu rõ giải pháp đường truyền vật lý riêng biệt cho doanh nghiệp.
  * ELB: Thấu hiểu cơ chế phân phối tải (Load Balancing) để đảm bảo hệ thống luôn sẵn sàng cao.

**1. Kiến trúc VPC và EC2 (Thứ 3)**
* Làm chủ kiến trúc và thiết lập hạ tầng mạng ảo (Amazon VPC): Khởi tạo thành công VPC tùy chỉnh (ASG VPC) theo chuẩn Multi-AZ, phân bổ Public/Private Subnet. Cấu hình Internet Gateway (IGW) và NAT Gateway để máy chủ Private truy cập Internet an toàn.
* Triển khai và vận hành hệ thống máy chủ ảo (Amazon EC2): Khởi tạo EC2 Instances trên môi trường Public và Private.
![VPC](/images/11.png)
* Quản trị truy cập và bảo mật mạng đa tầng: Cấu hình Security Groups, triển khai truy cập máy chủ nâng cao qua EIC Endpoint.
![Security Group](/images/12.png)
* Triển khai hệ thống giám sát: Ứng dụng VPC Reachability Analyzer, VPC Flow Logs và CloudWatch Monitoring.
![CloudWatch](/images/13.png)
![CloudWatch](/images/14.png)

**2. Hạ tầng kết nối Site-to-Site VPN (Thứ 4)**
* Thiết lập môi trường mạng On-premise mô phỏng bằng máy chủ EC2 đóng vai trò Customer Gateway (CGW). Khởi tạo Virtual Private Gateway (VGW) trên AWS.
![VPN](/images/15.png)
* Cấu hình VPN bằng cơ chế định tuyến tĩnh và khắc phục sự cố (Troubleshooting) thành công bằng Libreswan. Hai mạng ping thông suốt qua đường hầm IPsec.
![VPN](/images/16.png)

**3. AWS Session Manager & Kiểm toán (Thứ 5 - Phần 1)**
* Triển khai truy cập Zero-Trust với AWS Session Manager thông qua IAM Role và VPC Endpoints (ssm, ssmmessages, ec2messages) thay thế cho SSH.
![Session Manager](/images/17.png)
* Cấu hình S3 Bucket và S3 Gateway Endpoint để tự động lưu vết (Session Logs) đáp ứng yêu cầu kiểm toán.
![S3](/images/18.png)
* Ứng dụng Port Forwarding thiết lập kết nối RDP an toàn vào máy chủ Private Windows.
![RDP](/images/19.png)

**4. VPC Peering & Transit Gateway (Thứ 6)**
* Thiết lập kết nối nội bộ VPC Peering thành công giữa My VPC và HG VPC.
![VPC Peering](/images/20.png)
* Cấu hình Cross-Peer DNS để phân giải Public DNS chéo giữa 2 VPC.
![DNS](/images/21.png)
* Tối ưu hóa kiến trúc mạng bằng AWS Transit Gateway làm bộ định tuyến trung tâm cho 4 VPC độc lập.
![Transit Gateway](/images/22.png)
* Quản lý luồng định tuyến (Associations/Propagations) thành công, đảm bảo các máy chủ nhánh ping và SSH thông suốt.
![Transit Gateway](/images/23.png)

**5. Hybrid DNS với Route 53 & Microsoft AD (Thứ 5 - Phần 2)**
* Triển khai thành công dịch vụ AWS Managed Microsoft AD (giả lập DNS On-premises).
![Microsoft AD](/images/24.png)
* Cấu hình Route 53 Outbound Endpoint và Inbound Endpoint để đồng bộ phân giải tên miền hai chiều.
![Route 53](/images/25.png)
* Nghiệm thu phân giải tên miền chéo thành công từ máy chủ AWS sang mạng On-premises.
![Route 53](/images/26.png)
