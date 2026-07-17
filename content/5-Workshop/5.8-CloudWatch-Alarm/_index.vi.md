---
title : "Cấu hình CloudWatch Alarm & SNS Notification"
date : 2024-01-01 
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

Trong phần này, chúng ta sẽ thiết lập hệ thống **Email notification** thời gian thực sử dụng **Amazon SNS** phối hợp với **Amazon CloudWatch Alarm** khi số lượng requests đến **Application Load Balancer (ALB)** vượt quá ngưỡng **threshold** cấu hình.

#### Các bước thực hiện:

1. [Tạo SNS Topic & Subscribe Email](5.8.1-Create-SNS/)
2. [Tạo CloudWatch Alarm cho RequestCount](5.8.2-Create-Alarm/)
3. [Simulate Load & Kiểm thử Alarm](5.8.3-Load-Testing/)
