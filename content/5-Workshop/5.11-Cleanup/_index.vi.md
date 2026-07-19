---
title : "Dọn dẹp tài nguyên"
date : 2024-01-01 
weight : 11
chapter : false
pre : " <b> 5.11. </b> "
---

Để tránh phát sinh các chi phí không mong muốn trên tài khoản AWS của bạn sau khi hoàn tất bài thực hành, hãy tiến hành xóa sạch toàn bộ các tài nguyên đã khởi tạo theo đúng thứ tự hướng dẫn dưới đây.

---

### Bước 11.1: Xóa các ECS Services & Clusters
1. Vào dịch vụ **ECS** -> click chọn Cluster **`pg-cluster`**.
2. Chọn tab **Services**:
   - Tích chọn dịch vụ **`pg-frontend-service`** -> Click nút **Delete** -> Nhập dòng chữ xác nhận để xóa.
   - Tích chọn tiếp dịch vụ **`pg-backend-service`** -> Click nút **Delete** -> Xác nhận xóa.
3. Chờ cho các **Tasks** tắt hẳn.
4. Click chọn nút **Delete cluster** ở góc trên bên phải để xóa Cluster.

---

### Bước 11.2: Xóa Application Load Balancer & Target Groups
1. Vào dịch vụ **EC2** -> cuộn xuống mục **Load Balancing**:
   - Click chọn **Load Balancers** -> Tích chọn **`pg-alb`** -> Click **Actions** -> chọn **Delete load balancer** -> Xác nhận xóa.
   - Click tiếp **Target Groups** ở menu trái -> Tích chọn cả 2 Target Groups **`tg-frontend`** và **`tg-backend`** -> Click **Actions** -> chọn **Delete** -> Xác nhận xóa.

---

### Bước 11.3: Xóa RDS PostgreSQL Database
1. Vào dịch vụ **RDS** -> chọn **Databases** ở menu trái.
2. Tích chọn database **`pg-db`** của bạn.
3. Click chọn nút **Actions** -> chọn **Delete**.
4. Cấu hình trang xóa:
   - **Tắt ô chọn** *"Create final snapshot?"* (Không chụp final snapshot để tránh lưu giữ tính phí).
   - **Tích chọn ô** *"I acknowledge that..."* để xác nhận.
   - Nhập từ khóa xác nhận xóa (thường là `delete me`) vào ô trống.
5. Click nút **Delete** và chờ database xóa hoàn tất (thường mất 5-10 phút).
6. Click chọn tiếp mục **Subnet groups** ở menu trái RDS -> Chọn và xóa **`pg-db-subnet-group`**.

---

### Bước 11.4: Xóa NAT Gateway & Giải phóng Elastic IP
NAT Gateway là tài nguyên tính phí theo giờ rất cao nên cần phải xóa ngay lập tức:
1. Vào dịch vụ **VPC** -> chọn **NAT gateways** ở menu bên trái.
2. Tích chọn NAT Gateway **`pg-nat`** (hoặc NAT được sinh ra bởi Wizard VPC).
3. Click **Actions** -> chọn **Delete NAT gateway** -> Xác nhận xóa.
4. **Giải phóng Elastic IP:**
   - Chọn mục **Elastic IPs** ở menu trái VPC.
   - Tích chọn IP tĩnh đã liên kết với NAT gateway lúc trước.
   - Click **Actions** -> chọn **Release Elastic IP addresses** (Giải phóng IP tĩnh) -> Xác nhận giải phóng. *(Nếu không giải phóng IP tĩnh rác, AWS vẫn tính phí tài khoản của bạn)*.

---

### Bước 11.5: Xóa VPC
1. Tại dịch vụ **VPC**, chọn **Your VPCs** ở menu trái.
2. Tích chọn VPC **`pg-vpc`** của bạn.
3. Click chọn **Actions** -> chọn **Delete VPC**.
4. AWS sẽ tự động phân tích và xóa sạch toàn bộ Subnets, Internet Gateways, Route Tables và các nhóm bảo mật đi kèm với VPC này. Nhấn **Delete VPC** để xác nhận.

---

### Bước 11.6: Xóa ECR Repositories, S3 Bucket và KMS Key
1. **ECR Repositories:** Vào dịch vụ **ECR** -> Tích chọn 2 repositories `pg-combined-backend` và `pg-frontend` -> Nhấn **Delete** để xóa các Docker Images.
2. **S3 Bucket:**
   - Vào dịch vụ **S3** -> Click chọn S3 Bucket **`pg-db-backups-<account-id>-ap-southeast-1-an`**.
   - Click nút **Empty** để xóa toàn bộ các tệp snapshot bên trong -> Xác nhận.
   - Quay lại danh sách Bucket -> Tích chọn bucket đó và nhấn nút **Delete** -> Nhập tên bucket để xác nhận xóa vĩnh viễn.
3. **KMS Key:** Vào dịch vụ **KMS** -> click chọn khóa **`pg-s3-export-key`** -> click **Key actions** -> chọn **Schedule key deletion** -> Chọn số ngày tối thiểu (7 ngày) -> nhấn xác nhận.

Chúc mừng bạn đã hoàn thành bài thực hành một cách trọn vẹn và an toàn!
