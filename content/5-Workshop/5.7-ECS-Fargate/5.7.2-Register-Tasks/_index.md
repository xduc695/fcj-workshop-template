---
title : "Register Task Definitions"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

We will create **Task Definitions** in JSON format:
1. Go to the **ECS** service -> **Task definitions** in the left column -> click **Create new task definition** -> select **Create new task definition with JSON**.

2. **Register Task Definition for Backend (`pg-backend`):**
   - Delete the template code and paste the JSON below. 
   - *Note: Replace `<aws-account-id>` with your AWS account ID and `<rds-endpoint>`, `<yourpassword>` with your RDS PostgreSQL Endpoint and PostgreSQL password*:
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

![Backend Task Definitions configuration ](/images/h77.png)
   - Click **Create** to save.

3. **Register Task Definition for Frontend (`pg-frontend`):**
   - Click **Create new task definition with JSON** again and paste the following JSON:
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
![Frontend Task Definitions configuration ](/images/h78.png)
   - Click **Create** to complete.
