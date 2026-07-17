---
title : "Khởi tạo Database Instance PostgreSQL"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

Chúng ta sẽ khởi chạy một **RDS PostgreSQL DB Instance** trong **Private Subnets**, cấu hình không cấp phát địa chỉ **Public IP**.

---

### Các bước thực hiện:

1. Chọn mục **Databases** ở cột menu bên trái dịch vụ RDS -> nhấp nút **Create database** -> chọn **Standard create**.
2. Cấu hình các thông số:
   - **Choose a database creation method**: Chọn **Standard create**.
   - **Engine options**: Chọn **PostgreSQL**.
   - **Templates**: Chọn **Production** (hoặc **Free Tier**).
   - **Availability and durability**: Chọn **Multi-AZ DB instance deployment** (để tăng tính sẵn sàng).
   - **Settings**:
     - **DB instance identifier**: Nhập `pg-db`.
     - **Master username**: Nhập `postgres`.
     - **Credentials management**: Chọn **Self managed** và bỏ tích **Auto generate password**.
     - **Master password**: Nhập `12345678` (và xác nhận lại mật khẩu).
![Database RDS 1](/images/h19.png)
   - **Instance configuration**:
     - **DB instance class**: Chọn **Burstable classes** (bao gồm dòng t).
     - **Instance type**: Chọn cấu hình **`db.t3.micro`** (hoặc lớp phù hợp để tối ưu chi phí).
   - **Storage**:
     - **Storage type**: Chọn **General Purpose SSD (gp3)**.
     - **Allocated storage**: `20` GB (hoặc dung lượng phù hợp).
![Database RDS 2](/images/h20.png)
   - **Connectivity**:
     - **Virtual private cloud (VPC)**: Chọn **`pg-vpc`**.
     - **DB Subnet Group**: Chọn **`pg-db-subnet-group`** đã tạo ở bước trước.
     - **Public access**: Chọn **No** (Chỉ cho phép kết nối nội bộ để bảo mật tuyệt đối).
     - **VPC security group**: Chọn **Choose existing**, tích chọn **`pg-ecs-sg`** và bỏ chọn nhóm mặc định `default`.
![Database RDS 2](/images/h21.png)
3. Nhấp nút **Create database** ở dưới cùng.
4. Chờ 10-15 phút để database khởi tạo xong. Khi trạng thái chuyển sang màu xanh **Available**, click chọn tên database `pg-db` và sao chép địa chỉ **Endpoint** trong phần Connectivity (địa chỉ có dạng `pg-db.xxxx.ap-southeast-1.rds.amazonaws.com`).
