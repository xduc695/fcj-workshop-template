---
title : "Tích hợp S3 Backup & Recovery"
date : 2024-01-01 
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

Trong phần này, chúng ta sẽ thiết lập giải pháp **S3 Backup & Recovery** cho cơ sở dữ liệu: Chụp một **RDS Snapshot** và xuất dữ liệu đó sang **Amazon S3 Bucket**, được mã hóa bảo vệ bằng **KMS Key**.

#### Các bước thực hiện:

1. [Tạo S3 Bucket & KMS Key](5.9.1-S3-KMS-Setup/)
2. [Tạo IAM Policy & Role cho RDS](5.9.2-IAM-Policy-Role/)
3. [Chụp Snapshot & Export sang S3](5.9.3-Export-Snapshot/)
