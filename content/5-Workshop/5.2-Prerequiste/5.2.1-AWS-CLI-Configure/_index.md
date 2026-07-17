---
title : "Configure AWS CLI & Clone Source Code"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.2.1. </b> "
---

In this step, we will configure **AWS CLI Credentials** on your personal computer and download the Backend and Frontend project source code from Git to your machine.

---

### Step 1: Configure AWS CLI Credentials
Open the Terminal (MacOS/Linux) or PowerShell (Windows) on your computer and run the following command:
```bash
aws configure
```
Proceed to enter your **IAM User** information:
- **AWS Access Key ID**: Enter the provided Access Key ID
- **AWS Secret Access Key**: Enter the corresponding Secret Access Key
- **Default region name**: Enter your Region (For example: `ap-southeast-1`)
- **Default output format**: Enter `json`

![Cấu hình AWS CLI](/images/h1.png)

---

### Step 2: Clone Source Code
Use Git to download the project source code to your computer:

1. **Clone the Backend project:**
```bash
git clone https://github.com/LonggTran/high-concurrency-payment-gateway.git
```
2. **Clone the Frontend project:**
```bash
git clone https://github.com/xduc695/high-concurrency-payment-gateway-fe.git
```

![Clone mã nguồn thành công](/images/h2.png)
