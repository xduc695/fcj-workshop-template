---
title : "Biên dịch & Đẩy ảnh lên ECR"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2.2. </b> "
---

Trong bước này, chúng ta sẽ biên dịch dự án Spring Boot thành các file JAR, sau đó đóng gói thành các **Docker Images** và đẩy lên **AWS ECR Repositories**.

---

### Bước 1: Biên dịch mã nguồn Backend ra file JAR
1. Di chuyển vào thư mục gốc của dự án Backend:
```bash
cd high-concurrency-payment-gateway
```
2. Thực hiện biên dịch bằng Gradle (bỏ qua test):
```bash
./gradlew build -x test
```
*Đảm bảo quá trình hoàn tất thành công (BUILD SUCCESSFUL) để sinh ra các file JAR trong các thư mục `services/*/build/libs/`.*

![Gradle Build thành công](/images/h3.png)

---

### Bước 2: Tạo Private Repositories trên ECR
1. Truy cập AWS Console -> Tìm kiếm dịch vụ **Elastic Container Registry (ECR)**.
2. Click **Create repository**:
   - Chọn **Private**.
   - **Repository name**: `pg-combined-backend`. Click **Create**.
![Tạo ECR ](/images/h4.png)
3. Làm tương tự tạo repository thứ hai tên là: `pg-frontend`.
![Tạo ECR thành công](/images/h5.png)

---

### Bước 3: Đăng nhập Docker cục bộ và Push Docker Images lên AWS ECR
Chạy các lệnh Docker trong Terminal/PowerShell để build và đẩy ảnh (Thay `<aws-region>` bằng Region của bạn, ví dụ `ap-southeast-1`, và `<aws-account-id>` bằng ID tài khoản AWS của bạn):

1. **Xác thực Docker với ECR:**
```bash
aws ecr get-login-password --region <aws-region> | docker login --username AWS --password-stdin <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com
```
![Xác thực thành công](/images/h6.png)
2. **Build và Push ảnh Backend gộp:** (Chạy tại thư mục `high-concurrency-payment-gateway`)
```bash
# Build Docker Image Backend gộp
docker build -t pg-combined-backend -f backend.Dockerfile .

# Tag Docker Image
docker tag pg-combined-backend:latest <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-combined-backend:latest
# Push Docker Image lên ECR Repository
docker push <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-combined-backend:latest
```
![Build và Tag](/images/h7.png)
![Push](/images/h8.png)
3. **Build và Push ảnh Frontend:** (Chuyển sang thư mục `high-concurrency-payment-gateway-fe`)

Làm tương tự như với Backend:
```bash
cd ../high-concurrency-payment-gateway-fe

# Build Docker Image Frontend
docker build -t pg-frontend -f Dockerfile .

# Tag Docker Image
docker tag pg-frontend:latest <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-frontend:latest

# Push Docker Image lên ECR Repository
docker push <aws-account-id>.dkr.ecr.<aws-region>.amazonaws.com/pg-frontend:latest
```

![ECR images frontend](/images/h9.png)
![ECR images frontend](/images/h10.png)