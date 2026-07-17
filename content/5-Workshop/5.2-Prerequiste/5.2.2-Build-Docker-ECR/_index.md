---
title : "Compile & Push Images to ECR"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2.2. </b> "
---

In this step, we will compile the Spring Boot project into JAR files, then package them into **Docker Images** and push them to **AWS ECR Repositories**.

---

### Step 1: Compile Backend source code to JAR files
1. Navigate into the Backend project's root directory:
```bash
cd high-concurrency-payment-gateway
```
2. Perform compilation using Gradle (skip tests):
```bash
./gradlew build -x test
```
*Ensure the process completes successfully (BUILD SUCCESSFUL) to generate the JAR files in the `services/*/build/libs/` directories.*

![Gradle Build thành công](/images/h3.png)

---

### Step 2: Create Private Repositories on ECR
1. Access the AWS Console -> Search for the **Elastic Container Registry (ECR)** service.
2. Click **Create repository**:
   - Select **Private**.
   - **Repository name**: `pg-combined-backend`. Click **Create**.
![Tạo ECR ](/images/h4.png)
3. Do the same to create a second repository named: `pg-frontend`.
![Tạo ECR thành công](/images/h5.png)

---

### Step 3: Log in to Docker locally and Push Docker Images to AWS ECR
Run the Docker commands in Terminal/PowerShell to build and push images (Replace `<aws-region>` with your Region, e.g., `ap-southeast-1`, and `<aws-account-id>` with your AWS account ID):

1. **Authenticate Docker with ECR:**
```bash
aws ecr get-login-password --region <aws-region> | docker login --username AWS --password-stdin <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com
```
![Xác thực thành công](/images/h6.png)
2. **Build and Push the combined Backend image:** (Run in the `high-concurrency-payment-gateway` directory)
```bash
# Build combined Backend Docker Image
docker build -t pg-combined-backend -f backend.Dockerfile .

# Tag Docker Image
docker tag pg-combined-backend:latest <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-combined-backend:latest
# Push Docker Image to ECR Repository
docker push <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-combined-backend:latest
```
![Build và Tag](/images/h7.png)
![Push](/images/h8.png)
3. **Build and Push the Frontend image:** (Switch to the `high-concurrency-payment-gateway-fe` directory)

Do the same as with the Backend:
```bash
cd ../high-concurrency-payment-gateway-fe

# Build Frontend Docker Image
docker build -t pg-frontend -f Dockerfile .

# Tag Docker Image
docker tag pg-frontend:latest <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-frontend:latest

# Push Docker Image to ECR Repository
docker push <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-frontend:latest
```

![ECR images frontend](/images/h9.png)
![ECR images frontend](/images/h10.png)
