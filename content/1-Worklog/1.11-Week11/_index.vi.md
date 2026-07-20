---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

* Đóng gói mã nguồn ứng dụng bằng Docker và đẩy (push) các Docker Images lên Amazon ECR.
* Thiết lập hệ thống mạng VPC 3-tier (Public/Private Subnets), IGW, NAT Gateway và Security Groups bảo mật.
* Khởi tạo cơ sở dữ liệu Amazon RDS PostgreSQL trong Private Subnet và nạp schema qua EC2 Bastion Host.
* Triển khai cụm máy chủ container serverless AWS ECS Fargate và bộ cân bằng tải Application Load Balancer (ALB).
* Cấu hình hệ thống giám sát CloudWatch Alarms, SNS Notification và xuất bản sao lưu RDS Snapshot sang S3 Bucket mã hóa bằng KMS Key.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Đóng gói ứng dụng và quản lý ECR Repository:<br>&emsp; + Đóng gói mã nguồn Backend (Spring Boot) và Frontend (Nginx) bằng Docker.<br>&emsp; + Khởi tạo Amazon ECR Repositories (pg-backend, pg-frontend).<br>&emsp; + Build và push Docker Images từ môi trường phát triển lên Amazon ECR. | 29/06/2026 | 29/06/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.2-prerequiste/> |
| Thứ 3 | - Thiết lập hạ tầng mạng VPC và Security Groups:<br>&emsp; + Khởi tạo VPC 3-tier trên 2 Availability Zones (AZs) với Public/Private Subnets.<br>&emsp; + Cấu hình Internet Gateway (IGW) và NAT Gateway cho kết nối đi ra ngoài.<br>&emsp; + Thiết lập các Security Groups cách ly cho ALB, ECS Fargate, RDS và Bastion Host. | 30/06/2026 | 30/06/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.3-vpc-networking/><br><https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.4-security-groups/> |
| Thứ 4 | - Khởi tạo Cơ sở dữ liệu RDS PostgreSQL và Bastion Host:<br>&emsp; + Tạo DB Subnet Group và khởi tạo Amazon RDS PostgreSQL trong Private Subnet.<br>&emsp; + Khởi tạo máy chủ ảo EC2 Bastion Host tại Public Subnet.<br>&emsp; + Kết nối an toàn qua Bastion Host để nạp (initialize) SQL Schema cho RDS. | 01/07/2026 | 01/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.5-rds-database/>|
| Thứ 5 | - Cấu hình Load Balancer và triển khai ECS Fargate:<br>&emsp; + Khởi tạo Target Groups và Application Load Balancer (ALB) công khai.<br>&emsp; + Tạo ECS Cluster, định nghĩa Task Definitions (backend tích hợp Redis sidecar).<br>&emsp; + Triển khai ECS Services trên Fargate và cấu hình ECS Service Auto Scaling. | 02/07/2026 | 02/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.6-load-balancer/><br><https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.7-ecs-fargate/> |
| Thứ 6 | - Giám sát CloudWatch Alarm và cơ chế S3 Backup KMS:<br>&emsp; + Cấu hình Amazon SNS Topic gửi cảnh báo email khi hạ tầng quá tải.<br>&emsp; + Thiết lập CloudWatch Alarms theo dõi ngưỡng CPU utilization.<br>&emsp; + Khởi tạo S3 Bucket, KMS Key và thực hiện Export RDS Snapshot sang Amazon S3. | 03/07/2026 | 03/07/2026 |<https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.8-cloudwatch-alarm/><br><https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.9-s3-backup/> |

### Kết quả đạt được tuần 11:

**1. Đóng gói Container và Chuẩn hóa ECR Repository (Thứ 2)**
* Đóng gói thành công mã nguồn ứng dụng Backend Spring Boot và Frontend Nginx bằng Docker, tối ưu hóa kích thước image và thiết lập các biến môi trường cấu hình thống nhất.
* Khởi tạo các ECR Repositories (pg-backend, pg-frontend), thực hiện tag và push toàn bộ Docker Images từ môi trường phát triển lên đám mây Amazon ECR an toàn.

**2. Xây dựng Hạ tầng Mạng VPC 3-tier & Security Groups (Thứ 3)**
* Quy hoạch thành công hệ thống mạng VPC 3-tier phân tách trên 2 Availability Zones (AZs), cấu hình phân khu rõ ràng giữa Public Subnets, Private App Subnets và Private DB Subnets.
* Cấu hình Internet Gateway (IGW) cho tiếp nhận lưu lượng truy cập bên ngoài và NAT Gateway phục vụ các luồng mạng chủ động đi ra ngoài từ vùng Private Subnets.
* Thiết lập hệ thống tường lửa Security Groups phân lớp bảo mật chặt chẽ, áp dụng nguyên tắc đặc quyền tối thiểu (Least Privilege) giữa ALB, ECS Fargate, RDS và Bastion Host.

**3. Khởi tạo Cơ sở dữ liệu RDS PostgreSQL & Bastion Host (Thứ 4)**
* Khởi tạo cơ sở dữ liệu Amazon RDS PostgreSQL cô lập hoàn toàn trong vùng Private DB Subnet, thiết lập DB Subnet Group và cấu hình tham số lưu trữ bảo mật.
* Triển khai máy chủ ảo EC2 Bastion Host tại vùng Public Subnet làm cầu nối quản trị an toàn. Kết nối SSH thông suốt qua Bastion Host để khởi tạo (initialize) thành công toàn bộ SQL Schema và dữ liệu ban đầu cho RDS.

**4. Triển khai Bộ cân bằng tải ALB & ECS Fargate Container (Thứ 5)**
* Khởi tạo Application Load Balancer (ALB) công khai, cấu hình Target Groups và Listener Rules điều phối lưu lượng chính xác tới các cổng dịch vụ.
* Tạo ECS Cluster, định nghĩa các bản ghi Task Definitions cho Backend (tích hợp container Redis sidecar cho caching và lock) và Frontend Nginx.
* Triển khai ECS Services trên hạ tầng serverless AWS ECS Fargate thành công. ALB kiểm tra và xác nhận trạng thái Healthy hoạt động ổn định ở cổng 80 (Frontend) và cổng 8080 (Backend).
![Trạng thái Target Health của Backend](/images/h48.png)
![Trạng thái Target Health của Frontend](/images/h49.png)

**5. Giám sát CloudWatch Alarms & Xuất RDS Snapshot sang S3 bằng KMS (Thứ 6)**
* Khởi tạo kho lưu trữ Amazon S3 Data Bucket và tạo khóa KMS tự quản lý (Customer Managed KMS Key). Thực hiện thành công quá trình xuất (export) bản sao lưu RDS Snapshot sang S3 với cơ chế mã hóa dữ liệu ở trạng thái lưu trữ (Encryption at rest).
![Tạo S3 Bucket](/images/h61.png)
![Tạo khóa KMS](/images/h62.png)
![pg-db-snapshot-manual](/images/h65.png)
![Export to Amazon S3 success](/images/h68.png)
* Thiết lập Amazon SNS Topic đăng ký nhận email thông báo sự cố. Cấu hình hệ thống CloudWatch Alarms theo dõi chỉ số hạ tầng (CPU utilization), đảm bảo cảnh báo tự động phản hồi tức thì khi hệ thống tiệm cận ngưỡng quá tải.
![sns](/images/h50.png)
![Tạo CloudWatch Alarm](/images/h74.png)
