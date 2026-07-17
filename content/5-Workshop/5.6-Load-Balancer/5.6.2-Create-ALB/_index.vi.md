---
title : "Khởi tạo Application Load Balancer"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

Chúng ta sẽ khởi tạo **Application Load Balancer (ALB)** công cộng nằm ở 2 **Public Subnets** để tiếp nhận các yêu cầu truy cập từ Internet.

---

### Các bước thực hiện:

1. Ở cột menu bên trái EC2, nhấp vào mục **Load Balancers** -> nhấp nút **Create load balancer**.
2. Chọn loại **Application Load Balancer** -> nhấp **Create**.
3. Cấu hình các thông số:
   - **Load balancer name**: Nhập `pg-alb`.
   - **Scheme**: Chọn **Internet-facing** (Đón nhận traffic công cộng).
![Cấu hình Target Groups](/images/h31.png)
   - **Network mapping**:
     - **VPC**: Chọn **`pg-vpc`**.
     - **Mappings**: Tích chọn cả **2 Public Subnets** của bạn (`pg-subnet-public1...` ở AZ 1a và `pg-subnet-public2...` ở AZ 1b).
![Cấu hình Target Groups](/images/h32.png)
   - **Security groups**: Chọn Security Group **`pg-alb-sg`** (và gỡ bỏ nhóm mặc định `default`).
   - **Listeners and routing**:
     - Cổng listener mặc định: **HTTP:80** -> Chọn hành động forward đến Target Group **`tg-frontend`**.
![Cấu hình Target Groups](/images/h33.png)
4. Nhấp nút **Create load balancer** ở cuối trang và chờ trạng thái Load Balancer chuyển sang **Active**.

