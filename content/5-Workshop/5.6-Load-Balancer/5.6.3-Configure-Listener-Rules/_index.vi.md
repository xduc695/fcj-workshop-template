---
title : "Cấu hình Listener Rules cho API Gateway"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.6.3. </b> "
---

Để các API requests từ client (ví dụ `/api/accounts`) được gửi về API Gateway backend chứ không phải Frontend Nginx, chúng ta cấu hình **Listener Rule** để định tuyến.

---

### Các bước thực hiện:

1. Mở trang quản trị Load Balancers -> Click chọn vào tên `pg-alb` của bạn.
2. Chọn tab **Listeners and rules** ở giữa màn hình.
3. Click trực tiếp vào chữ **`HTTP:80`** (link liên kết màu xanh dương).
4. Chọn tab **Rules** -> nhấp vào nút **Add rules**.
5. Thiết lập thông số cho Rule mới:
   - **Rule name**: Nhập `api-rule`.
   - **Conditions**: Click **Add condition** -> chọn loại là **Path** -> nhập đường dẫn là **`/api/*`** -> nhấn **Next**.
   - **Actions**: Click **Forward to target groups** -> nhấp chọn Target Group **`tg-backend`** -> nhấn **Next**.
![Cấu hình Listener Rule](/images/h34.png)
   - **Priority**: Nhập số **`10`**.
![Cấu hình Listener Rule](/images/h35.png)
6. Nhấp nút **Add rule** để lưu lại.

