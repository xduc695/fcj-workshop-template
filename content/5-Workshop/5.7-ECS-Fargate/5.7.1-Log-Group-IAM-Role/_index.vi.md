---
title : "Chuẩn bị Log Group & IAM Role"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

Chúng ta cần tạo **CloudWatch Log Group** và **IAM Task Execution Role** để Fargate có thể chạy thành công và ghi logs.

---

### Bước 1: Tạo CloudWatch Log Group
Fargate sử dụng driver `awslogs` để ghi logs hệ thống, yêu cầu Log Group phải được tạo trước:
1. Tìm kiếm và chọn dịch vụ **CloudWatch** trên AWS Console.
2. Ở cột menu bên trái, chọn **Log groups** -> click **Create log group**.
3. **Log group name**: Nhập chính xác là **`/ecs/pg-logs`**.
4. **Retention setting**: Chọn **1 day** (hoặc 1 week) để tiết kiệm dung lượng. Nhấn **Create**.

![Tạo Log Group](/images/h36.png)

---

### Bước 2: Tạo IAM Task Execution Role thực thi Fargate (`ecsTaskExecutionRole`)
Role này cấp quyền cho ECS Agent pull Docker Images từ ECR và push logs lên CloudWatch:
1. Vào dịch vụ **IAM** -> chọn **Roles** ở menu trái -> click **Create role**.
2. **Trusted entity type**: Chọn **AWS service**.
3. **Service or use case**: Chọn **Elastic Container Service** -> Chọn **Elastic Container Service Task** ở dưới. Nhấn **Next**.
![IAM](/images/h37.png)
4. **Permissions policies**: Tìm kiếm và tích chọn policy **`AmazonECSTaskExecutionRolePolicy`**. Nhấn **Next**.
![IAM](/images/h38.png)
5. **Role name**: Nhập chính xác là: **`ecsTaskExecutionRole`**.
6. Nhấn **Create role** ở dưới cùng.

