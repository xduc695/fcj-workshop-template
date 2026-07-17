---
title : "Tạo các Target Groups"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

Chúng ta cần tạo 2 **Target Groups** tương ứng cho Frontend (port 80) và Backend (port 8080).

---

### Các bước thực hiện:

1. **Tạo Target Group cho Backend (`tg-backend`):**
   - Vào dịch vụ **EC2** -> cuộn menu trái xuống phần **Load Balancing** -> nhấp chọn **Target Groups** -> nhấn **Create target group**.
   - **Choose a target type**: Chọn **IP addresses** (Bắt buộc đối với ECS Fargate).
   - **Target group name**: Nhập `tg-backend`.
   - **Protocol & Port**: Chọn **HTTP** và điền cổng **`8080`** (Cổng của API Gateway).
![ cấu hình tg-backend 1](/images/h28.png)
   - **VPC**: Chọn **`pg-vpc`**.
   - **Health check path**: Nhập **`/actuator/health`** (Để check status của Spring Boot).
![ cấu hình tg-backend 1](/images/h29.png)
   - Nhấn **Next** -> Nhấp nút **Create target group**.

2. **Tạo Target Group cho Frontend (`tg-frontend`):**
   - Quay lại trang **Target Groups** -> nhấn **Create target group**.
   - **Choose a target type**: Tích chọn **IP addresses**.
   - **Target group name**: Nhập `tg-frontend`.
   - **Protocol & Port**: Chọn **HTTP** và điền cổng **`80`**.
   - **VPC**: Nhấp chọn **`pg-vpc`**.
   - **Health check path**: Nhập **`/`**.
   - Nhấn **Next** -> Nhấp nút **Create target group** (Bỏ qua bước đăng ký IP ở trang tiếp theo, ECS Service sẽ tự động đăng ký IP của Task khi khởi chạy).
![Danh sách Target Groups](/images/h30.png)
