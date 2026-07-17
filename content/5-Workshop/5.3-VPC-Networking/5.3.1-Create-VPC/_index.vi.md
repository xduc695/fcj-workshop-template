---
title : "Khởi tạo VPC với \"VPC and more\""
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

Chúng ta sử dụng trình cấu hình tự động "VPC and more" để dựng toàn bộ sơ đồ mạng Public và Private Subnets.

---

### Bước 1: Tạo VPC
1. Đăng nhập vào AWS Console -> Tìm kiếm và chọn dịch vụ **VPC**.
2. Nhấp vào nút **Create VPC** ở góc trên bên phải.
3. Cấu hình các thông số:
   - **Resources to create**: Chọn **VPC and more**.
   - **Name tag auto-generation**: Nhập tiền tố là **`pg`**.
   - **IPv4 CIDR block**: Giữ nguyên **`10.0.0.0/16`**.
![cấu hình vpc 1](/images/h11.png)

   - **Number of Availability Zones (AZs)**: Chọn **2**.
   - **Number of Public Subnets**: Chọn **2**.
   - **Number of Private Subnets**: Chọn **2**.
   - **NAT Gateways**: Chọn **1 in 1 AZ**.
   - **VPC Endpoints**: Chọn **None**.
   - **DNS options**: Đảm bảo đã tích chọn cả hai ô **Enable DNS resolution** và **Enable DNS hostnames**.
![cấu hình vpc 2](/images/h75.png)
4. Click **Create VPC** ở dưới cùng để khởi tạo VPC.

![Tạo VPC thành công](/images/h13.png)

---

### Bước 2: Enable Public IP cho các Public Subnets
Để đảm bảo ALB và Bastion Host tự động nhận Public IP:
1. Click chọn **Subnets** ở menu trái.
2. Tích chọn subnet công cộng thứ nhất: `pg-subnet-public1-ap-southeast-1a`.
3. Click chọn **Actions** -> chọn **Edit subnet settings**.
4. Tích chọn **Enable auto-assign public IPv4 address**. Nhấn **Save**.
![Bật IP Public](/images/h14.png)
5. Làm tương tự đối với subnet công cộng thứ hai: `pg-subnet-public2-ap-southeast-1b`.
