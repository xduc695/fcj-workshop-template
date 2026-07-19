---
title : "Giới thiệu"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về Hệ thống High-Concurrency Payment Gateway

Hệ thống High-Concurrency Payment Gateway được triển khai trong bài thực hành này là một ứng dụng microservices được xây dựng bằng **Spring Boot** (cho Backend) và **React Vite** (cho Frontend). Dự án bao gồm các dịch vụ thành phần:
- **API Gateway (Port 8080):** Tiếp nhận toàn bộ các request từ bên ngoài và route đến các dịch vụ nội bộ tương ứng.
- **Account Service (Port 8082):** Quản lý tài khoản khách hàng, đăng ký và số dư (Balance).
- **Payment Service (Port 8083):** Thực hiện xử lý giao dịch thanh toán và nạp/rút tiền tích hợp cơ chế chống trùng lặp (Idempotency) sử dụng **Redis Distributed Lock**.
- **Transaction Service (Port 8084):** Quản lý lịch sử giao dịch và đối soát tài khoản (Ledger).
- **Redis Cache/Lock:** Lưu trữ các lock phân tán chống trùng lắp giao dịch.

#### Sơ đồ Kiến trúc Mạng bảo mật (Private Subnet)

Mô hình triển khai trên AWS áp dụng cơ chế bảo mật cô lập:

![diagram](/images/diagram.jpg)

#### Các điểm nổi bật của kiến trúc:
1. **Network Isolation:** Application Load Balancer (ALB) đón nhận traffic công cộng tại tầng **Public Subnet**, trong khi đó các ECS Tasks và Cơ sở dữ liệu RDS PostgreSQL chạy hoàn toàn trong mạng **Private Subnet** nhằm ngăn ngừa nguy cơ bị quét cổng hoặc tấn công trực tiếp.
2. **NAT Gateway:** Các ECS Tasks đặt trong Private Subnet không có Public IP nhưng vẫn kết nối Outbound ra Internet thông qua NAT Gateway để kéo ảnh Docker và đẩy CloudWatch Logs.
3. **Monolithic Task:** 4 microservices backend được gộp chung trong một Docker Image chạy đồng thời với Redis container (sidecar) trong cùng một ECS Task giúp tối ưu hóa chi phí vận hành Fargate.
4. **S3 Backup:** Sao lưu RDS PostgreSQL an toàn thông qua tính năng RDS Snapshot Export mã hóa bằng KMS Key sang Amazon S3.
