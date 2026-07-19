---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
# High-Concurrency Payment Gateway Infrastructure on AWS  
## Hạ tầng Cổng thanh toán Hiệu năng cao bảo mật 3 lớp với ECS Fargate và S3 Backup  

### 1. Tóm tắt điều hành  
Hệ thống **High-Concurrency Payment Gateway** được thiết kế nhằm cung cấp một hạ tầng cổng thanh toán trực tuyến bảo mật, chịu tải tốt và có khả năng phục hồi thảm họa cao trên nền tảng AWS. Dự án này phục vụ việc chuyển đổi mô hình ứng dụng Payment Gateway Microservices từ môi trường phát triển cục bộ lên hạ tầng đám mây đạt tiêu chuẩn Production-ready. Hạ tầng áp dụng mô hình phân tách mạng **VPC 3-tier (Public/Private Subnets)** kết hợp giữa **Application Load Balancer (ALB)**, **AWS ECS Fargate** cho serverless containers (Frontend Nginx, Spring Boot Backend và Redis sidecar), cơ sở dữ liệu **Amazon RDS PostgreSQL** cô lập, hệ thống giám sát CloudWatch Alarm cùng cơ chế tự động hóa **S3 Backup & Recovery** sử dụng khóa KMS tùy chỉnh.

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Các hệ thống cổng thanh toán truyền thống chạy trên on-premises hoặc máy ảo đơn lẻ thường đối mặt với các thách thức:
- **Rủi ro bảo mật:** Database và API chứa thông tin tài chính nhạy cảm bị phơi bày trực tiếp ra Internet công cộng (Public IP).
- **Khả năng chịu tải kém:** Khó mở rộng tự động (Auto Scaling) khi lượng requests thanh toán tăng đột biến (flash sales), dẫn đến nghẽn mạng và treo hệ thống.
- **Thiếu giám sát thời gian thực:** Không có hệ thống cảnh báo tức thời khi hệ thống quá tải hoặc lỗi container.
- **Rủi ro mất mát dữ liệu:** Quy trình backup database thực hiện thủ công, lưu trữ phân tán và không được mã hóa bảo vệ.

*Giải pháp*  
Hạ tầng mới thiết lập trên AWS giải quyết triệt để các vấn đề trên:
- **Network Isolation:** Toàn bộ container Backend và RDS Database chạy cô lập 100% trong **Private Subnets**, giao tiếp ra ngoài Internet một chiều qua **NAT Gateway**.
- **Serverless Compute:** Sử dụng **AWS ECS Fargate** để quản trị container tự động, giảm thiểu gánh nặng quản lý máy ảo EC2 OS.
- **High Availability & Routing:** Sử dụng **Application Load Balancer (ALB)** đặt tại **Public Subnets** để tiếp nhận traffic HTTP (port 80) từ Internet, tự động chuyển hướng các API requests (`/api/*`) về API Gateway Backend (port 8080) và các requests tĩnh về Frontend Nginx.
- **Real-time Alerting:** Cấu hình **CloudWatch Alarm** kết hợp **Amazon SNS** gửi Email notification trực tiếp tới quản trị viên khi phát hiện lượng traffic vượt ngưỡng (RequestCount > 100 requests/phút).
- **Secure Backup:** Sử dụng **Customer Managed Key (KMS Symmetric)** để mã hóa các bản Snapshot cơ sở dữ liệu RDS và tự động xuất (Export) sang **Amazon S3 Bucket** làm data lake lưu trữ lâu dài.
- **EC2 Bastion Host:** Dựng máy ảo Jumpbox tạm thời ở Public Subnet chỉ khi cần nạp database schema ban đầu, sau đó terminate ngay để tối ưu chi phí và bảo mật.

*Lợi ích và hoàn vốn đầu tư (ROI)*  
- **An toàn bảo mật tối đa:** Đạt tiêu chuẩn an toàn dữ liệu tài chính nhờ cô lập mạng lưới và mã hóa KMS.
- **Giảm thời gian chết (Downtime):** Tự động phát hiện lỗi qua Target Group Health Check của ALB để tự động phục hồi (Recreate) container bị lỗi.
- **Hiệu quả chi phí:** Nhờ tính năng serverless của Fargate và cơ chế tắt/xóa tài nguyên thừa, chi phí vận hành ước tính dao động khoảng 100 - 120 USD/tháng cho môi trường test tải trọng lớn, mang lại hiệu quả ROI vượt trội so với việc tự xây dựng hạ tầng vật lý tại on-premises.

### 3. Kiến trúc giải pháp  
Hạ tầng Payment Gateway áp dụng kiến trúc mạng 3 lớp (Public, Private App, Private DB) chạy hoàn toàn trên AWS.

![diagram](/images/diagram.jpg)

*Dịch vụ AWS sử dụng*  
- *Amazon VPC*: Quản lý hạ tầng mạng ảo gồm 4 Subnets, Route Tables, Internet Gateway và NAT Gateway.
- *AWS ECS Fargate*: Dịch vụ container không máy chủ chạy ứng dụng Frontend và Backend.
- *Amazon RDS (PostgreSQL)*: Cơ sở dữ liệu quan hệ được quản trị toàn phần chạy trong Private Subnets.
- *Amazon S3*: Nơi lưu trữ các bản xuất Snapshot nén của database.
- *AWS Key Management Service (KMS)*: Tạo Customer Managed Key để mã hóa snapshot xuất khẩu.
- *Amazon CloudWatch*: Thu thập logs từ container (`/ecs/pg-logs`) và tạo cảnh báo hiệu năng `RequestCount`.
- *Amazon SNS*: Gửi thông tin Email cảnh báo thời gian thực.
- *Amazon EC2*: Sử dụng cho Bastion Host trung chuyển dữ liệu.

*Thiết kế thành phần*  
- **Frontend Task**: Container Nginx phục vụ giao diện NextGenPay tĩnh, nhận traffic chuyển tiếp từ ALB ở cổng 80.
- **Backend Task**: Chạy mô hình Multi-Container gồm container Java/Spring Boot (gộp API Gateway, Account, Payment, Transaction Service) và container Redis sidecar làm cache tốc độ cao trên cùng mạng `localhost`.
- **Database & Backup**: RDS PostgreSQL lưu trữ dữ liệu tài khoản và giao dịch, định kỳ chụp Snapshot thủ công/tự động và xuất sang S3 Bucket dưới dạng nén được mã hóa bởi KMS Key `pg-s3-export-key`.

### 4. Triển khai kỹ thuật  
*Các giai đoạn triển khai*  
Dự án được xây dựng và triển khai qua 4 giai đoạn chính:
1. *Nghiên cứu ứng dụng & Thiết kế hạ tầng*: Đóng gói mã nguồn Backend Gradle và Frontend Next.js/HTML thành các Docker Images, thiết kế sơ đồ mạng VPC 3 lớp trên AWS.
2. *Thiết lập mạng lưới & Cơ sở dữ liệu*: Khởi dựng VPC, Route Tables, NAT Gateway, Security Groups và Database RDS PostgreSQL Private. Sử dụng Bastion Host nạp schema SQL.
3. *Triển khai Container & Định tuyến ALB*: Thiết lập Target Groups, ALB Listener Rules, đăng ký Task Definitions JSON và chạy ECS Services (Frontend & Backend).
4. *Cấu hình Giám sát & Backup S3*: Thiết lập CloudWatch Alarm cho chỉ số RequestCount, liên kết SNS Topic gửi Mail cảnh báo. Tạo KMS Key, cấu hình IAM Policy/Role và tiến hành export Snapshot cơ sở dữ liệu sang S3 an toàn.

### 5. Lộ trình & Mốc triển khai  
- *Tuần 1*: Đóng gói mã nguồn dự án thành Docker Images, đẩy lên AWS ECR Private Repositories. Thiết lập VPC mạng 3 lớp, NAT Gateway và Security Groups.
- *Tuần 2*: Khởi tạo RDS PostgreSQL trong mạng Private. Dựng Bastion Host để kết nối và chạy script SQL khởi tạo. Tạo Target Groups và cấu hình ALB Listener Rules định tuyến phân tách `/api/*`.
- *Tuần 3*: Đăng ký ECS Task Definitions cho Frontend và Backend, khởi chạy ECS Services. Tạo hệ thống cảnh báo CloudWatch Alarm & SNS Notification.
- *Tuần 4*: Thiết lập KMS Customer Managed Key, gán IAM permissions và chạy quy trình xuất RDS Snapshot sang S3 Bucket. Kiểm thử toàn bộ hệ thống bằng script test tải trọng và dọn dẹp tài nguyên.

### 6. Ước tính ngân sách  
Ước tính chi phí vận hành cho môi trường thử nghiệm cổng thanh toán trong 1 tháng (dựa trên AWS Pricing Calculator):

*Chi phí hạ tầng*  
- **VPC NAT Gateway:** ~32,40 USD/tháng (0,045 USD/giờ cho 1 AZ).
- **Application Load Balancer (ALB):** ~16,20 USD/tháng (0,0225 USD/giờ).
- **Amazon RDS (db.t3.micro Multi-AZ PostgreSQL):** ~26,28 USD/tháng (lớp db.t3.micro kèm ổ SSD gp3 20GB).
- **AWS ECS Fargate Tasks (CPU & RAM):** ~30,00 USD/tháng (Backend Task 1 vCPU/2GB RAM và Frontend Task 0.25 vCPU/0.5GB RAM chạy liên tục).
- **AWS KMS Key:** 1,00 USD/tháng.
- **Amazon S3 & CloudWatch Logs:** ~3,00 USD/tháng (lưu trữ logs và file nén backup).
- **Amazon SNS:** 0,00 USD/tháng (trong hạn mức Free Tier).

*Tổng chi phí ước tính:* ~110 USD/tháng (~1.320 USD/năm).

### 7. Đánh giá rủi ro  
*Ma trận rủi ro*  
- **Quá tải requests (DDoS/Flash Sale):** Ảnh hưởng cao, xác suất trung bình.
- **Lỗi kết nối cơ sở dữ liệu (Database Down):** Ảnh hưởng rất cao, xác suất thấp.
- **Lọt lộ thông tin credentials/KMS Key:** Ảnh hưởng rất cao, xác suất thấp.

*Chiến lược giảm thiểu*  
- **Quá tải requests:** Sử dụng CloudWatch Alarm cảnh báo tức thời qua mail để quản trị viên kịp thời tăng số lượng Task (Auto Scaling) hoặc giới hạn băng thông.
- **Lỗi Database:** Khởi chạy RDS dưới dạng Multi-AZ để tự động chuyển vùng dự phòng (Failover) khi xảy ra sự cố phần cứng.
- **Lọt lộ dữ liệu:** Giới hạn IAM Roles nghiêm ngặt, sử dụng Custom KMS Key Policy để chỉ cho phép RDS Service Assume Role xuất dữ liệu.

### 8. Kết quả kỳ vọng  
*Cải tiến kỹ thuật*  
- **Bảo mật mạng toàn diện:** Loại bỏ hoàn toàn IP công cộng cho Backend và DB, bảo vệ bằng các lớp Security Group chặt chẽ.
- **Giám sát trực quan:** Toàn bộ hoạt động của microservices được tập trung hóa logs và theo dõi thông tin tài nguyên theo thời gian thực.
- **Sao lưu tin cậy:** Có tệp tin snapshot lưu trữ an toàn trên S3, bảo vệ bằng mã hóa chuẩn doanh nghiệp.

*Giá trị dài hạn*  
Nền tảng hạ tầng DevOps vững chắc cho phép mở rộng quy mô dự án lên nhiều microservices khác, dễ dàng chuyển đổi sang sử dụng Terraform/CloudFormation (IaC) để tự động hóa toàn bộ quy trình triển khai trong tương lai.