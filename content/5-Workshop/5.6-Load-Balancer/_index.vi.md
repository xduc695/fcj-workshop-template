---
title : "Cấu hình Application Load Balancer"
date : 2024-01-01 
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

Trong phần này, chúng ta sẽ thiết lập **Application Load Balancer (ALB)** công cộng để route traffic từ Internet: Mặc định chuyển về Frontend (port 80), còn các API requests có đường dẫn `/api/*` sẽ chuyển về API Gateway Backend (port 8080).

#### Các bước thực hiện:

1. [Tạo các Target Groups](5.6.1-Create-Target-Groups/)
2. [Khởi tạo Application Load Balancer](5.6.2-Create-ALB/)
3. [Cấu hình Listener Rules cho API Gateway](5.6.3-Configure-Listener-Rules/)
