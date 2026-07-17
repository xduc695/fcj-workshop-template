---
title : "Initialize Database qua EC2 Bastion Host"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

Vì RDS database bị khóa trong Private Subnets, máy tính cá nhân ở nhà không thể kết nối trực tiếp để nạp schema. Chúng ta sẽ dựng một **EC2 Bastion Host** làm cầu nối tạm thời ở mạng Public.

---

### Bước 1: Khởi chạy EC2 Bastion Host
1. Tìm kiếm và chọn dịch vụ **EC2** -> chọn mục **Instances** -> click nút **Launch instances**.
2. Thiết lập thông số:
   - **Name**: Nhập `pg-bastion`.
   - **OS**: Chọn **Amazon Linux 2023** (Bản Free Tier eligible).
   - **Instance type**: Chọn `t2.micro` (hoặc `t3.micro`).
   - **Key pair**: Chọn **Proceed without a key pair** (chúng ta sẽ kết nối trực tiếp qua trình duyệt web).
![Cấu hình ec2 1](/images/h22.png)
   - **Network settings**: Click **Edit**:
     - **VPC**: Chọn **`pg-vpc`**.
     - **Subnet**: Chọn public subnet đầu tiên (Ví dụ `pg-subnet-public1-ap-southeast-1a`).
     - **Auto-assign public IP**: Chọn **Enable**.
     - **Security group**: Chọn **Create security group** -> Đặt tên: `pg-bastion-sg` -> Phần Inbound rule: Bắt buộc chọn Source là **`0.0.0.0/0`** (Anywhere IPv4) cho cổng 22 SSH để có thể dùng tính năng EC2 Instance Connect trên trình duyệt.
![Cấu hình ec2 2](/images/h23.png)
3. Click nút **Launch instance**.

---

### Bước 2: Cho phép Bastion Host truy cập RDS
1. Vào Security Group **`pg-ecs-sg`** -> click **Edit inbound rules** -> Nhấn **Add rule**:
   - **Type**: Chọn **PostgreSQL** (port 5432).
   - **Source**: Chọn **Custom** -> chọn Security Group **`pg-bastion-sg`** của Bastion Host vừa tạo. Nhấn **Save rules**.

---

### Bước 3: Đăng nhập và chạy lệnh SQL bằng trình duyệt
![Cấu hình Cho phép Bastion Host truy cập RDS](/images/h24.png)
1. Tại trang EC2 Instances, chọn máy ảo `pg-bastion` -> nhấn nút **Connect** ở góc trên.
![connect ec2](/images/h25.png)
2. Chọn tab **EC2 Instance Connect** -> nhấn nút **Connect**. Một màn hình terminal Linux màu đen sẽ hiển thị trực tiếp trên trình duyệt của bạn!
3. Chạy các lệnh sau trong terminal để cài đặt postgresql client và nạp dữ liệu:
   ```bash
   # 1. Cài đặt psql client
   sudo dnf install postgresql15 -y

   # 2. Tạo tệp chứa câu lệnh SQL khởi tạo
   cat << 'EOF' > init.sql
   CREATE DATABASE paymentservice;
   CREATE DATABASE accountservice;
   CREATE DATABASE transactionservice;
   EOF
   
   # 3. Thực thi lệnh nạp database lên RDS (thay <rds-endpoint> bằng địa chỉ Endpoint RDS của bạn)
   # Khi hệ thống hỏi Password, hãy nhập: yourpassword (khi gõ mật khẩu sẽ ẩn đi, bạn cứ gõ đúng rồi nhấn Enter)
   psql -h <rds-endpoint> -U postgres -d postgres -f init.sql
   ```  
![ Cài đặt psql client](/images/h26.png)  
![ Tạo và thực thi nạp db lên rds](/images/h27.png)
   *Quá trình nạp thành công sẽ báo `CREATE DATABASE` cho 3 cơ sở dữ liệu.*

4. **Terminate EC2 Bastion Host sau khi nạp xong:**
   - Quay lại trang quản trị EC2 Instances -> Chọn máy ảo `pg-bastion` -> Chọn **Instance state** -> chọn **Terminate instance** để xóa máy ảo đi tránh phát sinh chi phí.
