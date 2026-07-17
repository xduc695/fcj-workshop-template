---
title : "Khởi tạo RDS PostgreSQL trong mạng Private"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Trong phần này, chúng ta sẽ thiết lập **Amazon RDS PostgreSQL** chạy cô lập hoàn toàn trong **Private Subnets** và dùng một **EC2 Bastion Host** ở **Public Subnet** để tiến hành initialize database schema ban đầu.

#### Các bước thực hiện:

1. [Tạo DB Subnet Group](5.5.1-Create-Subnet-Group/)
2. [Khởi tạo Database Instance PostgreSQL](5.5.2-Create-RDS-Instance/)
3. [Initialize Database qua Bastion Host](5.5.3-Initialize-Database/)
