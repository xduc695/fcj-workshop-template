---
title : "Đăng ký các Task Definitions"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

Chúng ta sẽ tạo các **Task Definitions** dưới dạng JSON:
1. Vào dịch vụ **ECS** -> **Task definitions** ở cột trái -> nhấp **Create new task definition** -> chọn **Create new task definition with JSON**.

2. **Đăng ký Task Definition cho Backend (`pg-backend`):**
   - Xóa code mẫu và dán đoạn JSON dưới đây vào. 
   - *Lưu ý: Thay thế `<aws-account-id>` bằng ID tài khoản AWS của bạn và `<rds-endpoint>` , `<yourpassword>` bằng Endpoint RDS PostgreSQL và mật khẩu PostgreSQL của bạn*:
```json
{
  "family": "pg-backend",
  "cpu": "1024",
  "memory": "2048",
  "networkMode": "awsvpc",
  "requiresCompatibilities": ["FARGATE"],
  "executionRoleArn": "arn:aws:iam::<aws-account-id>:role/ecsTaskExecutionRole",
  "containerDefinitions": [
    {
      "name": "backend",
      "image": "<aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-combined-backend:latest",
      "cpu": 768,
      "memory": 1536,
      "portMappings": [
        {"containerPort": 8080},
        {"containerPort": 8082},
        {"containerPort": 8083},
        {"containerPort": 8084}
      ],
      "environment": [
        {"name": "SPRING_PROFILES_ACTIVE", "value": "dev"},
        {"name": "DB_USERNAME", "value": "postgres"},
        {"name": "DB_PASSWORD", "value": "<yourpassword>"},
        {"name": "DB_ACCOUNT_NAME_URL", "value": "jdbc:postgresql://<rds-endpoint>:5432/accountservice"},
        {"name": "DB_PAYMENT_NAME_URL", "value": "jdbc:postgresql://<rds-endpoint>:5432/paymentservice"},
        {"name": "DB_TRANSACTION_NAME_URL", "value": "jdbc:postgresql://<rds-endpoint>:5432/transactionservice"},
        {"name": "REDIS_HOST", "value": "127.0.0.1"},
        {"name": "REDIS_PORT", "value": "6379"},
        {"name": "ACCOUNT_SERVICE_URL", "value": "http://localhost:8082"},
        {"name": "PAYMENT_SERVICE_URL", "value": "http://localhost:8083"},
        {"name": "TRANSACTION_SERVICE_URL", "value": "http://localhost:8084"}
      ],
      "logConfiguration": {
        "logDriver": "awslogs",
        "options": {
          "awslogs-group": "/ecs/pg-logs",
          "awslogs-region": "<aws-region>",
          "awslogs-stream-prefix": "backend"
        }
      }
    },
    {
      "name": "redis",
      "image": "public.ecr.aws/docker/library/redis:alpine",
      "cpu": 256,
      "memory": 512,
      "portMappings": [
        {"containerPort": 6379}
      ],
      "logConfiguration": {
        "logDriver": "awslogs",
        "options": {
          "awslogs-group": "/ecs/pg-logs",
          "awslogs-region": "<aws-region>",
          "awslogs-stream-prefix": "redis"
        }
      }
    }
  ]
}
```

![Cấu hình Task Definitions backend ](/images/h77.png)
   - Nhấn **Create** để lưu lại.

3. **Đăng ký Task Definition cho Frontend (`pg-frontend`):**
   - Click chọn **Create new task definition with JSON** một lần nữa và dán đoạn JSON sau vào:
```json
{
  "family": "pg-frontend",
  "cpu": "256",
  "memory": "512",
  "networkMode": "awsvpc",
  "requiresCompatibilities": ["FARGATE"],
  "executionRoleArn": "arn:aws:iam::<aws-account-id>:role/ecsTaskExecutionRole",
  "containerDefinitions": [
    {
      "name": "frontend",
      "image": "<aws-account-id>.dkr.ecr.ap-southeast-1.amazonaws.com/pg-frontend:latest",
      "cpu": 256,
      "memory": 512,
      "portMappings": [
        {"containerPort": 80}
      ],
      "logConfiguration": {
        "logDriver": "awslogs",
        "options": {
          "awslogs-group": "/ecs/pg-logs",
          "awslogs-region": "ap-southeast-1",
          "awslogs-stream-prefix": "frontend"
        }
      }
    }
  ]
}
```
![Cấu hình Task Definitions frontend ](/images/h78.png)
   - Nhấn **Create** để hoàn tất.

