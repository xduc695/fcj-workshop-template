---
title : "Cấu hình AWS CLI & Clone Source Code"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.2.1. </b> "
---

Trong bước này, chúng ta sẽ cấu hình **AWS CLI Credentials** trên máy tính cá nhân và tải mã nguồn dự án Backend và Frontend từ Git về máy.

---

### Bước 1: Cấu hình AWS CLI Credentials
Mở Terminal (MacOS/Linux) hoặc PowerShell (Windows) trên máy tính của bạn và chạy lệnh sau:
```bash
aws configure
```
Tiến hành nhập các thông tin **IAM User** của bạn:
- **AWS Access Key ID**: Nhập Access Key ID được cấp
- **AWS Secret Access Key**: Nhập Secret Access Key tương ứng
- **Default region name**: Nhập Region của bạn (Ví dụ: `ap-southeast-1`)
- **Default output format**: Nhập `json`

![Cấu hình AWS CLI](/images/h1.png)

---

### Bước 2: Clone Source Code
Sử dụng Git để tải mã nguồn dự án về máy tính của bạn:

1. **Clone dự án Backend:**
```bash
git clone https://github.com/LonggTran/high-concurrency-payment-gateway.git
```
2. **Clone dự án Frontend:**
```bash
git clone https://github.com/xduc695/high-concurrency-payment-gateway-fe.git
```

![Clone mã nguồn thành công](/images/h2.png)
