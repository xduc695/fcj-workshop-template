---
title : "Tạo DB Subnet Group"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

**DB Subnet Group** quy định các subnets mà RDS instance được phép sử dụng. Chúng ta sẽ giới hạn RDS chỉ chạy trong các **Private Subnets**.

---

### Các bước thực hiện:

1. Tìm kiếm và chọn dịch vụ **RDS** trên thanh tìm kiếm của AWS Console.
2. Ở cột menu bên trái, nhấp vào mục **Subnet groups** -> nhấp nút **Create DB subnet group**.
3. Thiết lập thông số:
   - **Name**: Nhập `pg-db-subnet-group`.
   - **Description**: Nhập `DB Subnet Group for payment gateway`.
   - **VPC**: Nhấp chọn **`pg-vpc`**.
   - **Add subnets**:
     - **Availability Zones**: Chọn 2 AZs (ví dụ `ap-southeast-1a` và `ap-southeast-1b`).
     - **Subnets**: Tích chọn 2 **Private Subnets** có dải IP **`10.0.128.0/20`** và **`10.0.144.0/20`** (được tạo tự động từ bước VPC).

![Tạo DB Subnet Group](/images/h18.png)
4. Nhấp nút **Create** ở dưới cùng.


