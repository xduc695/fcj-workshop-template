---
title : "Khởi chạy các ECS Services"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.7.3. </b> "
---

Trong phần này, chúng ta sẽ tiến hành tạo **ECS Cluster** và khởi chạy các **ECS Services** trong các **Private Subnets**.

---

### Bước 1: Tạo ECS Cluster
1. Chọn **Clusters** ở menu trái -> click **Create cluster**.
2. **Cluster name**: Nhập `pg-cluster`.
3. **Infrastructure**: Chọn **Fargate only (serverless)**. Nhấn **Create**.

---

![Tạo ECS Cluster](/images/h41.png)
![Tạo ECS Cluster thành công](/images/h42.png)
### Bước 2: Khởi chạy Service Backend (`pg-backend-service`)
1. Vào Cluster `pg-cluster` -> tab **Services** -> chọn **Create**.
2. Cấu hình:
   - **Task definition family**: Chọn **`pg-backend`** (revision mới nhất).
   - **Service name**: Nhập `pg-backend-service`.
   - **Task definition revision**: Nhập `1`.
![`pg-backend-service](/images/h43.png)
   - **Deployment configuration**: 
     - **Health check grace period**: Nhập `300`.
   - **Networking**:
     - **VPC**: Chọn **`pg-vpc`**.
     - **Subnets**: Tích chọn **chỉ 2 Private Subnets** của bạn (Ví dụ: `pg-subnet-private1...` và `pg-subnet-private2...`). *Hãy bỏ chọn các Public Subnets*.
     - **Security group**: Chọn **Use existing Security group** -> chọn **`pg-ecs-sg`** (xóa nhóm mặc định `default`).
     - **Public IP**: Đảm bảo đã chọn **Turned off**.
![`pg-backend-service](/images/h44.png)
   - **Load balancing**:
     - **Load balancer type**: Chọn **Application Load Balancer**.
     - **Load balancer**: Chọn **`pg-alb`**.
     - **Container to load balance**: Chọn container `backend:8080:8080`.
![`pg-backend-service](/images/h45.png)
     - **Listener**: Chọn **Use an existing listener** -> chọn **`HTTP:80`**.
     - **Target group**: Chọn **Use an existing target group** -> chọn **`tg-backend`**.
![`pg-backend-service](/images/h46.png)  
   - **Service auto scaling**:
     - **Minimum number of tasks**: **`1`**.
     - **Maximum number of tasks**: **`5`**.
     - **Scaling policy type**: Chọn **Target tracking**.
     - **Policy name** : Nhập **`cpu-auto-scaling`**.
     - **ECS service metric**: Chọn **ECSServiceAverageCPUUtilization**.
     - **Target value**: Nhập **`70`**.
     - **Scale-out cooldown period**: Nhập **`60`**.
     - **Scale-in cooldown period**: Nhập **`300`**.
     - **Turn off scale-in**: Bỏ chọn 
![`pg-backend-service](/images/h71.png) 
3. Nhấn **Create**.

---

### Bước 3: Khởi chạy Service Frontend (`pg-frontend-service`)
1. Quay lại Cluster -> click **Create** dịch vụ thứ hai.
2. Cấu hình:
   - **Task definition family**: **`pg-frontend`** | **Service name**: `pg-frontend-service` | **Task definition revision**: `1`.
   - **Networking**: VPC `pg-vpc`, chỉ chọn 2 **Private Subnets**, Security Group `pg-ecs-sg`, Public IP: **Turned off**.
   - **Load balancing**:
     - **Load balancer**: Chọn `pg-alb`.
     - **Container**: Chọn container `frontend:80:80`.
     - **Listener**: Chọn **Use an existing listener** -> chọn **`HTTP:80`**.
     - **Target group**: Chọn **Use an existing target group** -> chọn **`tg-frontend`**.
3. Nhấn **Create**.

*Chờ khoảng 1-2 phút, trạng thái cả 2 Services sẽ chuyển sang Running (màu xanh). Lúc này bạn có thể dùng DNS của ALB để truy cập giao diện web!*
![pg-backend-service](/images/h48.png)
![pg-backend-service](/images/h49.png)
![Dịch vụ Fargate chạy thành công và triển khai thành công](/images/h47.png)
