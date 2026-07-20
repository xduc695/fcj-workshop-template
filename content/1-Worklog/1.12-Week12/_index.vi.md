---
title: "Worklog Tuần 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Mục tiêu tuần 12:

* Hoàn thiện tài liệu hướng dẫn thực hành (Workshop 10 phần) chi tiết hướng dẫn người dùng cuối trên AWS Console.
* Tổng hợp kiến thức và hoàn thiện các bài Báo cáo thu hoạch sự kiện FCJ Community Day và Blog công nghệ chuyên sâu.
* Thực hiện kiểm thử tải giả lập (k6) và đánh giá năng lực chịu tải thông qua hệ thống giám sát CloudWatch (Logs, Metrics, Alarms).
* Biên soạn Bản đề xuất dự án (Proposal), lập dự toán chi phí vận hành và thực hiện tự đánh giá năng lực (Self-Evaluation).
* Tổng kiểm tra, đóng gói toàn bộ hệ thống tài liệu và bàn giao dự án lên GitHub Repository.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Hoàn thiện tài liệu Workshop thực hành (Step-by-step):<br>&emsp; + Biên soạn 10 phần tài liệu hướng dẫn thực hành (Workshop).<br>&emsp; + Mô tả chi tiết từng bước nhấp chuột trên AWS Console từ VPC, RDS, ALB đến ECS Fargate và S3 Backup. | 06/07/2026 | 06/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/> |
| Thứ 3 | - Báo cáo Chuỗi sự kiện và Viết Blog kỹ thuật:<br>&emsp; + Viết 03 bài báo cáo thu hoạch chuỗi sự kiện FCJ Community Day (AI, GenAI, WebSockets).<br>&emsp; + Biên soạn 03 bài Blog chuyên sâu về DevOps, Cloud Operations và FinOps. | 07/07/2026 | 07/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/3-blogstranslated/><br><https://xduc695.github.io/fcj-workshop-template/vi/4-eventparticipated/> |
| Thứ 4 | - Thực hiện kiểm thử tải giả lập và giám sát hiệu năng:<br>&emsp; + Triển khai kịch bản giả lập tải k6 với 100 VUs liên tục tạo 10.000 giao dịch thanh toán.<br>&emsp; + Kiểm tra trạng thái Target Groups của ALB, biểu đồ RequestCount và CloudWatch Alarms.<br>&emsp; + Bóc tách CloudWatch Log Streams (/ecs/pg-logs) để đánh giá độ trễ và toàn vẹn dữ liệu. | 08/07/2026 | 08/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/5-workshop/5.10-verification/> |
| Thứ 5 | - Biên soạn Bản đề xuất dự án (Proposal):<br>&emsp; + Viết mới Bản đề xuất dự án (Proposal) tích hợp sơ đồ kiến trúc 3 lớp bảo mật.<br>&emsp; + Lập bảng dự toán chi phí vận hành chi tiết bằng AWS Pricing Calculator. | 09/07/2026 | 09/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/2-proposal/> |
| Thứ 6 | - Tự đánh giá năng lực và đóng gói báo cáo cuối khóa:<br>&emsp; + Thực hiện tự đánh giá năng lực (Self-Evaluation) và viết bài đóng góp ý kiến (Feedback).<br>&emsp; + Kiểm tra hiển thị hình ảnh, định dạng Markdown và cấu trúc Hugo.<br>&emsp; + Commit và Push toàn bộ source code lên GitHub Repository sẵn sàng nghiệm thu. | 10/07/2026 | 10/07/2026 | <https://xduc695.github.io/fcj-workshop-template/vi/6-self-evaluation/><br><https://xduc695.github.io/fcj-workshop-template/vi/7-feedback/> |

### Kết quả đạt được tuần 12:

**1. Chuỗi tài liệu Workshop và Báo cáo Blog (Thứ 2 - Thứ 3)**
* Soạn thảo chi tiết 10 phần hướng dẫn thực hành Workshop bằng thuật ngữ tiếng Anh chuyên ngành chuẩn xác.
* Hoàn thiện 03 bài báo cáo thu hoạch sự kiện FCJ Community Day và 03 bài Blog chia sẻ chuyên môn lên cộng đồng AWS Study Group VN.

**2. Kiểm thử Tải giả lập và Giám sát CloudWatch (Thứ 4)**
* Truy cập ứng dụng thành công qua DNS của Application Load Balancer để kiểm thử nghiệp vụ trên trình duyệt.
![Web High-Concurrency Payment Gateway](/images/h82.png)
![Kiểm toán tài khoản](/images/h84.png)
![Giả lập kiểm thử](/images/h85.png)
* Kiểm tra CloudWatch Log Group /ecs/pg-logs. Bóc tách thành công các log khởi chạy của Spring Boot, ghi nhận kết nối tới PostgreSQL và Redis sidecar.
![Log Streams backend](/images/h86.png)
* Giám sát lượng requests qua ALB bằng metrics RequestCount (Sum, 1 minutes). Biểu đồ trực quan tăng vọt chứng minh lượng traffic từ công cụ kiểm thử.
![Metrics RequestCount](/images/h87.png)
* **Kết quả K6:** Hệ thống đương đầu thành công 100 VUs tạo 10.000 giao dịch trong 1 phút 50 giây (Tỷ lệ thành công 99.78%). Cơ chế khóa phân tán bảo toàn tính nhất quán (delta = 0.00).
![Kết quả toàn vẹn dữ liệu k6](/images/h88.png)
* Các cảm biến Alarm hoạt động nhạy bén: AlarmLow (CPU < 63%) và AlarmHigh (CPU > 70%) được trigger chuẩn xác phục vụ Auto Scaling.
![Trạng thái CloudWatch Alarms](/images/h89.png)

**3. Bản đề xuất Proposal & Tự đánh giá Năng lực (Thứ 5 - Thứ 6)**
* Viết mới hoàn toàn trang Bản đề xuất (Proposal) tích hợp sơ đồ kiến trúc Mermaid 3 lớp bảo mật và bảng dự toán chi phí (~100 USD/tháng).
* Hoàn thiện bài Tự đánh giá năng lực (Self-Evaluation) và bài đóng góp ý kiến (Feedback) song ngữ Anh - Việt.

**4. Tổng kiểm tra & Đóng gói Báo cáo Cuối khóa (Thứ 6)**
* Rà soát 100% các file ảnh, đảm bảo toàn bộ hệ thống tài liệu Markdown được hiển thị đẹp mắt.
* Biên dịch Hugo server local thành công, đẩy toàn bộ mã nguồn lên GitHub sẵn sàng nghiệm thu dự án.
