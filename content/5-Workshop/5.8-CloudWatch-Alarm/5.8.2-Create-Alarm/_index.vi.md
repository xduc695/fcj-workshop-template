---
title : "Tạo CloudWatch Alarm cho RequestCount"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.8.2. </b> "
---

Chúng ta sẽ thiết lập **CloudWatch Alarm** để giám sát tổng số requests gửi đến ALB.

---

### Các bước thực hiện:

1. Tìm kiếm và mở dịch vụ **CloudWatch** trên AWS Console.
2. Cột menu bên trái, chọn **Alarms** -> chọn **All alarms** -> nhấp nút **Create alarm** ở góc phải.
3. Click chọn **Select metric**:
   - Chọn mục **ApplicationELB** -> chọn tiếp **Per AppELB Metrics**.
   - Nhập tìm kiếm và tích chọn dòng metric có tên **`RequestCount`** tương ứng với Load Balancer **`pg-alb`** của bạn.
   - Nhấp nút **Select metric** ở dưới cùng.
![Alarms](/images/h72.png)
4. **Cấu hình Metric và Alarm Threshold (QUAN TRỌNG):**
   - **Statistic**: Chọn **`Sum`** (Tổng số) - *Tuyệt đối không chọn Average*.
   - **Period**: Chọn **`1 minute`** (Để hệ thống cập nhật nhanh chóng sau mỗi phút).
   - **Threshold type**: Chọn **Static**.
   - **Whenever RequestCount is...**: Chọn **Greater than threshold** | **than...**: Điền **`1000`** (Báo động khi có trên 1000 requests/phút).
![Alarms](/images/h73.png)
   - Nhấp **Next**.
5. **Cấu hình Actions:**
   - **Alarm state trigger**: Chọn **In alarm**.
   - **Send a notification to the following SNS topic**: Chọn **Select an existing SNS topic** -> Nhấp chọn chủ đề **`pg-alerts`** của bạn.
   - *Đảm bảo rằng tính năng Actions enabled đã được kích hoạt*. Nhấp **Next**.
![Alarms](/images/h56.png)
6. **Đặt tên cho Alarm:** Nhập `pg-alb-high-request-alarm`. 
Nhấp **Next** -> Nhấp **Create alarm** ở dưới cùng.

![Tạo CloudWatch Alarm](/images/h74.png)
