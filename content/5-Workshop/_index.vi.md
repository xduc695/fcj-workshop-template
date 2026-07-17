---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Triển khai Hệ thống Thanh toán hiệu năng cao trên AWS ECS Fargate với Private Subnets, RDS PostgreSQL và S3 Backup

#### Tổng quan

Trong workshop này, chúng ta sẽ cùng nhau tự tay xây dựng và triển khai một hệ thống hạ tầng đám mây hoàn chỉnh, bảo mật và chịu tải cao trên AWS cho một ứng dụng **Payment Gateway Microservices**.

Hệ thống sẽ được thiết kế theo các tiêu chuẩn bảo mật doanh nghiệp bao gồm phân lập **Public/Private Subnets**, sử dụng **Application Load Balancer (ALB)** để nhận và route traffic, chạy các **microservices backend** gộp kèm **Redis sidecar** trên **AWS ECS Fargate**, kết nối với cơ sở dữ liệu **Amazon RDS PostgreSQL** chạy nội bộ và thiết lập cơ chế **S3 Backup & Recovery** qua tính năng **Snapshot Export** kết hợp với **KMS Key**.

#### Nội dung thực hành

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị môi trường & AWS ECR](5.2-Prerequiste/)
3. [Thiết lập mạng lưới VPC](5.3-VPC-Networking/)
4. [Thiết lập Security Groups](5.4-Security-Groups/)
5. [Khởi tạo RDS PostgreSQL trong mạng Private](5.5-RDS-Database/)
6. [Cấu hình Application Load Balancer](5.6-Load-Balancer/)
7. [Triển khai ECS Fargate](5.7-ECS-Fargate/)
8. [Cấu hình CloudWatch Alarm & SNS Notification](5.8-CloudWatch-Alarm/)
9. [Tích hợp S3 Backup & Recovery](5.9-S3-Backup/)
10. [Kiểm tra & Nghiệm thu](5.10-Verification/)
11. [Dọn dẹp tài nguyên](5.11-Cleanup/)