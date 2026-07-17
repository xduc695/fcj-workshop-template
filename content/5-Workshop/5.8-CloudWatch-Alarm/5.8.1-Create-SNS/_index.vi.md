---
title : "Tạo SNS Topic & Subscribe Email"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.8.1. </b> "
---

Chúng ta sẽ tạo **SNS Topic** để AWS có một kênh gửi email thông báo tự động.

---

### Các bước thực hiện:

1. Tìm kiếm và mở dịch vụ **Simple Notification Service (SNS)** trên AWS Console.
2. Click chọn **Topics** ở menu bên trái -> nhấp nút **Create topic**.
3. Cấu hình Topic:
   - **Type**: Chọn **Standard**.
   - **Name**: Nhập `pg-alerts`.
![sns](/images/h50.png)
   - Nhấp nút **Create topic** ở dưới cùng.
4. **Tạo Subscription để subscribe Email:**
   - Tại trang chi tiết của topic `pg-alerts` vừa tạo, nhấp chọn nút **Create subscription** ở bảng phía dưới.
   - **Protocol**: Chọn **Email**.
   - **Endpoint**: Nhập **địa chỉ email thực tế** của bạn.
   - Nhấp nút **Create subscription**.
![sns](/images/h51.png)
5. **Confirm Subscription:**
   - Mở hòm thư email của bạn, tìm thư được gửi từ AWS Notifications với tiêu đề *"AWS Notification - Subscription Confirmation"*.
   - Mở thư và click vào liên kết **Confirm Subscription** để kích hoạt.

![Xác nhận email SNS](/images/h52.png)
