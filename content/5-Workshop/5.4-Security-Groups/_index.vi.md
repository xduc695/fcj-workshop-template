---
title : "Thiết lập Security Groups"
date : 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

Trong phần này, chúng ta sẽ tạo các **Security Groups** để hoạt động như một virtual firewall kiểm soát lưu lượng truy cập ra/vào Application Load Balancer, các ECS Tasks và Cơ sở dữ liệu RDS.

---

### Bước 4.1: Tạo Security Group cho Application Load Balancer (`pg-alb-sg`)
ALB sẽ là chốt chặn đón traffic trực tiếp từ Internet gửi tới hệ thống:
1. Mở dịch vụ **EC2** trên AWS Console -> Cuộn menu bên trái xuống phần **Network & Security** -> click chọn **Security Groups**.
2. Nhấp vào nút **Create security group** ở góc phải màn hình.
3. Thiết lập thông tin:
   - **Security group name**: Nhập `pg-alb-sg`.
   - **Description**: Nhập `Allow HTTP traffic from internet`.
   - **VPC**: Nhấp chọn **`pg-vpc`** (Tuyệt đối không chọn VPC mặc định).
4. **Cấu hình Inbound rules:** Nhấp chọn **Add rule**:
   - **Type**: Chọn **HTTP** (port 80).
   - **Source**: Chọn **Anywhere-IPv4** (`0.0.0.0/0`) để cho phép mọi người truy cập.
5. Nhấp nút **Create security group** ở dưới cùng.

![Tạo Security Group cho ALB](/images/h16.png)

---

### Bước 4.2: Tạo Security Group cho Containers & Database (`pg-ecs-sg`)
Security Group này sẽ bảo vệ các Fargate Tasks chạy Frontend, Backend gộp và database RDS PostgreSQL trong mạng Private:
1. Quay lại trang Security Groups -> Nhấp vào nút **Create security group**.
2. Thiết lập thông tin:
   - **Security group name**: Nhập `pg-ecs-sg`.
   - **Description**: Nhập `Allow traffic from ALB and internal containers`.
   - **VPC**: Nhấp chọn **`pg-vpc`**.
3. **Cấu hình Inbound rules:** Thêm 4 luật cụ thể sau để đảm bảo phân quyền chặt chẽ:
   - **Rule 1 (Cho Frontend):** Type: **HTTP** | Source: Chọn **Custom** -> chọn Security Group **`pg-alb-sg`** vừa tạo ở Bước 4.1.
   - **Rule 2 (Cho API Gateway Backend):** Type: Chọn **Custom TCP** | Port range: Nhập `8080` | Source: Chọn **Custom** -> chọn Security Group **`pg-alb-sg`**.
   - **Rule 3 (Cho Database PostgreSQL):** Type: Chọn **PostgreSQL** (port 5432) | Source: Chọn **Custom** -> chọn chính Security Group **`pg-ecs-sg`** đang tạo này. (Cách này giúp container Backend liên kết chung SG có quyền gọi tới RDS).
   - **Rule 4 (Kết nối nội bộ):** Type: Chọn **All traffic** | Source: Chọn **Custom** -> chọn chính Security Group **`pg-ecs-sg`** đang tạo này. (Giúp container Java kết nối chéo với container Redis sidecar trên cùng một task).
4. Nhấp nút **Create security group** ở dưới cùng.
![ Security Group cho ECS và RDS](/images/h17.png)