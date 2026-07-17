---
title : "Thiết lập VPC Networking"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

Trong phần này, chúng ta sẽ thiết lập hạ tầng **VPC Networking** bằng tính năng **"VPC and more"** để tạo nhanh 4 Subnets (2 Public Subnets cho Load Balancer và 2 Private Subnets cho ECS Tasks/RDS Database), cùng Internet Gateway và NAT Gateway.

#### Các bước thực hiện:

1. [Khởi tạo VPC với "VPC and more"](5.3.1-Create-VPC/)
2. [Cấu hình Routing cho NAT Gateway](5.3.2-Subnet-Route-NAT/)
