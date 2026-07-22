---
title : "Kiểm tra & Nghiệm thu"
date : 2024-01-01 
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

Sau khi đã triển khai toàn bộ các thành phần hạ tầng (VPC, RDS, ALB, ECS Fargate, CloudWatch Alarm, S3 Backup), đây là bước cuối cùng để kiểm thử và nghiệm thu tính đúng đắn của toàn bộ hệ thống.

> **Video Demo:** Để xem trực quan toàn bộ quá trình tương tác giao diện và chạy giả lập kiểm thử k6 trên hạ tầng AWS, vui lòng truy cập [Video Demo & Kiểm thử hệ thống](https://drive.google.com/file/d/1J2bgKGyZWc86H7bJlQ3_K-vSoPuC1VAp/view?usp=sharing).

---

### Bước 10.1: Kiểm tra trạng thái Target Groups của ALB
Trước khi truy cập giao diện web, chúng ta cần đảm bảo Application Load Balancer đã nhận diện và kết nối thành công đến các Fargate Tasks trong mạng Private:
1. Vào dịch vụ **EC2** -> Chọn **Target Groups** ở menu bên trái.
2. Kiểm tra trạng thái sức khỏe của cả 2 Target Groups:
   - **`tg-frontend`**: Ở tab **Targets**, danh sách IP của Task Frontend phải hiển thị trạng thái **`Healthy`** ở cổng 80.
   - **`tg-backend`**: Danh sách IP của Task Backend phải hiển thị trạng thái **`Healthy`** ở cổng 8080.

![Trạng thái Target Health của Backend](/images/h48.png)
![Trạng thái Target Health của Frontend](/images/h49.png)

---

### Bước 10.2: Truy cập và Kiểm thử Giao diện Web
1. Vào dịch vụ **EC2** -> Chọn **Load Balancers** -> Click chọn **`pg-alb`**.
2. Sao chép địa chỉ **DNS name**
3. Dán địa chỉ DNS này vào trình duyệt web để truy cập giao diện **High-Concurrency Payment Gateway**:

![web](/images/h82.png)
![thanh toán và kiểm toán tài khoản](/images/h84.png)
![giả lập kiểm thử cơ bản](/images/h85.png)
---

### Bước 10.3: Kiểm tra Logs của Container bằng CloudWatch
Để kiểm tra xem các microservices có hoạt động ổn định và kết nối chéo thành công:
1. Vào dịch vụ **CloudWatch** trên AWS Console.
2. Chọn **Log groups** ở menu bên trái -> Click vào Log Group **`/ecs/pg-logs`** mà chúng ta đã cấu hình trong Task Definitions.
3. Kiểm tra các **Log Streams** tương ứng với từng container:
   - **`backend/...`**: Chứa nhật ký khởi chạy của ứng dụng Spring Boot (API Gateway, Account Service, Payment Service, Transaction Service). Bạn sẽ thấy log kết nối thành công tới database PostgreSQL (`pg-db`) và Redis sidecar (`127.0.0.1:6379`).
   - **`redis/...`**: Chứa nhật ký của Redis sidecar chạy cùng Task.
   - **`frontend/...`**: Chứa logs hoạt động của Nginx web server phân phối giao diện tĩnh.

---
![Log Streams backend](/images/h86.png)
### Bước 10.4: Xem Metrics số lượng Requests trên CloudWatch
Chúng ta có thể xem biểu đồ trực quan về lượng requests thực tế đi qua Application Load Balancer:
1. Tại dịch vụ **CloudWatch**, chọn **Metrics** -> chọn **All metrics** ở menu trái.
2. Tìm kiếm và chọn chỉ số **`RequestCount`** tương ứng với Load Balancer **`pg-alb`** (hoặc chọn tab **Graphed metrics** để tùy chỉnh thời gian hiển thị).
3. Chọn **Statistic** là **`Sum`** và **Period** là **`5 minutes`** (hoặc `1 minute`). Biểu đồ trực quan hóa số lượng requests đi qua hệ thống sẽ hiển thị tương tự hình dưới:

![Metrics](/images/h87.png)

- Biểu đồ sẽ hiển thị đường đồ thị tăng vọt lên (ví dụ lên tới gần 5500 requests) tại thời điểm bạn chạy lệnh PowerShell giả lập tải để kiểm thử CloudWatch Alarm.

---

### Bước 10.5: Đánh giá Kết quả Khả năng chịu tải và Co giãn tự động (Load Testing & Auto Scaling)
Sau khi thực hiện bài kiểm tra giả lập tải cường độ cao bằng k6, chúng ta sẽ xem xét các số liệu đạt được để nghiệm thu năng lực của kiến trúc Microservices trên AWS.

1. **Khả năng chịu tải đồng thời cực cao (High Concurrency):**
   - Dựa trên màn hình tổng kết (Summary), hệ thống đã đương đầu thành công với kịch bản cực đoan: **100 người dùng ảo (VUs)** liên tục tạo **10.000 giao dịch** thanh toán.
   - **Tốc độ xử lý:** Toàn bộ quá trình kiểm tra số dư, trừ tiền, và lưu lịch sử qua 3 microservices được giải quyết trọn vẹn trong vỏn vẹn **1 phút 50 giây**.
   - Tỷ lệ xử lý thành công đạt **99.78%**. Chỉ có một lượng rất nhỏ (0.22%) bị hệ thống API Gateway và Redis Rate Limiter chủ động chặn lại nhằm bảo vệ máy chủ khỏi nguy cơ quá tải (Overload Protection).

2. **Tính toàn vẹn dữ liệu tuyệt đối (Data Invariant & Distributed Lock):**
   - Quan sát mục `PAYMENT INVARIANT CHECK` trong kết quả:
   - Dù có hàng nghìn giao dịch cùng tranh chấp trừ tiền trên cùng một tài khoản, số dư cuối cùng trong cơ sở dữ liệu khớp tuyệt đối (Sai số `delta = 0.00`).
   - Kết quả này khẳng định cơ chế **Khóa phân tán (Redis Distributed Lock)** và tính **Lũy đẳng (Idempotency)** đã hoạt động hoàn hảo, không xảy ra bất kỳ hiện tượng thất thoát hay sai lệch dữ liệu (Race Condition) nào.

![Kết quả toàn vẹn dữ liệu k6](/images/h88.png)

3. **Cơ chế giám sát và Tự động co giãn (CloudWatch & Auto Scaling):**
   - Từ màn hình **CloudWatch Alarms**, các cảm biến hoạt động vô cùng nhạy bén:
     - **AlarmLow (`CPU < 63%`):** Chuyển trạng thái `In alarm` chính xác khi hệ thống vắng khách để thu hồi bớt máy chủ nhằm tiết kiệm chi phí.
     - **AlarmHigh (`CPU > 70%`):** Được hệ thống giám sát chặt chẽ. Nhờ khả năng xử lý vượt trội của Fargate (1 vCPU, 2GB RAM), hệ thống đã "nuốt trọn" 10.000 requests trước khi chạm ngưỡng thời gian để kích hoạt sinh thêm máy chủ.

![Trạng thái CloudWatch Alarms](/images/h89.png)

**Kết luận:** Hệ thống High-Concurrency Payment Gateway đã hoàn toàn sẵn sàng cho môi trường Production, đáp ứng xuất sắc các tiêu chuẩn khắt khe nhất về độ tin cậy (Reliability), khả năng mở rộng (Scalability) và tính nhất quán dữ liệu (Consistency).