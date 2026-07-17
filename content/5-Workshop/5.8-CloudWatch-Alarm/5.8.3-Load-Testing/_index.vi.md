---
title : "Simulate Load & Kiểm thử Alarm"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.8.3. </b> "
---

Chúng ta sẽ giả lập gửi lượng lớn requests để kích hoạt **CloudWatch Alarm** và nhận **Email notification**.

---

### Bước 1: Kích hoạt giả lập tải
Chạy PowerShell Script từ máy tính cá nhân (thay thế địa chỉ DNS của ALB của bạn):
```powershell
k6 run -e VUS=100 -e ITERATIONS=10000 -e ACCOUNT_IDS="<YOUR_ACCOUNT_UUID>" -e PAYMENT_BASE_URL="http://<YOUR_ALB_URL>" -e ACCOUNT_BASE_URL="http://<YOUR_ALB_URL>" payment_system_k6.js
```

---
![gửi request từ PowerShell cục bộ](/images/h79.png)
* Lưu ý: Bạn cũng có thể dùng các công cụ benchmark khác để gửi requests.

### Bước 2: Kiểm thử kết quả
1. Chờ khoảng 1-2 phút.
2. Kiểm tra **CloudWatch Alarm** `pg-alb-high-request-alarm`: Status sẽ chuyển sang màu đỏ báo **`In alarm`**.
![CloudWatch Alarm In Alarm](/images/h80.png)
3. Mở hòm thư email của bạn: Bạn sẽ nhận được email cảnh báo tự động từ AWS SNS.

![CloudWatch Alarm In Alarm](/images/h81.png)
