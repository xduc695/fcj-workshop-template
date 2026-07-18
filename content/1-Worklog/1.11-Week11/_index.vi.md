---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

* Dịch chuyển ứng dụng High-Concurrency Payment Gateway lên hạ tầng đám mây AWS (ECS Fargate, RDS, ALB, S3 KMS Export).
* Thực hiện kiểm thử tải giả lập (k6) và đánh giá năng lực chịu tải, tính toàn vẹn dữ liệu thông qua hệ thống giám sát CloudWatch (Logs, Metrics, Alarms).
* Xây dựng tài liệu hướng dẫn thực hành (Workshop) chi tiết hướng dẫn người dùng cuối trên AWS Console.
* Tổng hợp kiến thức và hoàn thiện 03 bài báo cáo thu hoạch chi tiết về chuỗi sự kiện công nghệ *FCJ Community Day*.
* Hệ thống hóa kiến thức thực chiến và hoàn thiện báo cáo về 03 bài viết Blog chuyên sâu đã đăng tải trên cộng đồng AWS Study Group VN.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Triển khai và kiểm thử hạ tầng ứng dụng thực chiến lên đám mây AWS:<br> - **Thực hành:** <br>&emsp; + Đóng gói Docker Images (Backend & Frontend) đẩy lên ECR.<br>&emsp; + Khởi chạy dịch vụ trên ECS Fargate.<br>&emsp; + Thiết lập RDS PostgreSQL cô lập trong Private Subnet và nạp schema qua EC2 Bastion Host.<br>&emsp; + Cấu hình giải pháp xuất RDS Snapshot định kỳ sang Amazon S3 bằng KMS Key. | 29/06/2026 | 29/06/2026 | <https://calculator.aws/> |
| Thứ 3 | - Thực hiện kiểm thử tải giả lập và giám sát hiệu năng trên AWS:<br> - **Thực hành:** <br>&emsp; + Triển khai kịch bản giả lập tải k6 với 100 VUs liên tục tạo 10.000 giao dịch thanh toán.<br>&emsp; + Kiểm tra trạng thái Target Groups của ALB (Frontend, Backend).<br>&emsp; + Giám sát biểu đồ RequestCount và trạng thái Alarm trên CloudWatch.<br>&emsp; + Kiểm tra log ALB và CloudWatch Log Streams (`/ecs/pg-logs`) để đánh giá tỷ lệ lỗi. | 30/06/2026 | 30/06/2026 | |
| Thứ 4 | - Hoàn thiện tài liệu Workshop thực hành (Step-by-step):<br> - **Thực hành:** <br>&emsp; + Biên soạn 10 phần tài liệu hướng dẫn thực hành (Workshop).<br>&emsp; + Mô tả chi tiết từng bước nhấp chuột trên AWS Console để build toàn bộ kiến trúc 3 lớp bảo mật. | 01/07/2026 | 01/07/2026 | |
| Thứ 5 | - Viết bài thu hoạch Event 1: Tổng quan AI, Cloud & Chuẩn Software Engineering (Kiến trúc AI, Prompt Engineering, hệ thống Agent). <br> - Viết bài thu hoạch Event 2: Lộ trình tự học AWS, GenAI Pipeline cho Startup và DevOps (Chuyển dịch Serverless, GenAI 3 lớp, DevOps Foundation). <br> - Viết bài thu hoạch Event 3: Kiến trúc thời gian thực, GraphRAG, An ninh mạng ML và Dịch chuyển sự nghiệp (WebSocket, GraphRAG, LightGBM, DevOps). | 02/07/2026 | 02/07/2026 | |
| Thứ 6 | - Biên soạn bài Blog 1: Tự động hóa CI/CD với GitHub Actions và Amazon ECS Express Mode (OIDC, tự động tag image, ECS AWS Fargate). <br> - Biên soạn bài Blog 2: Phục hồi thảm họa cho Stateful Services trên Amazon EKS bằng Velero (Tệp .tar.gz S3, EBS Snapshots, lỗi kẹt Pod). <br> - Biên soạn bài Blog 3: Tối ưu chi phí với EC2 Capacity Manager và Amazon Athena (Parquet S3, Partition Projection, 3 kịch bản SQL FinOps). | 03/07/2026 | 03/07/2026 | |

### Kết quả đạt được tuần 11:

**1. Triển khai Hạ tầng Ứng dụng lên AWS (Thứ 2)**
* Đóng gói mã nguồn Backend Gradle và Frontend Nginx đẩy lên AWS ECR. Triển khai thành công lên cụm ECS Fargate chạy an toàn bên trong các Private Subnets.
* Khởi tạo database RDS PostgreSQL cô lập hoàn toàn, kết nối thông suốt qua JDBC và nạp schema SQL thông qua cầu nối an toàn EC2 Bastion Host.
* Thiết lập giải pháp khôi phục thảm họa: cấu hình IAM policy/role cho phép export dữ liệu nén RDS Snapshot bảo vệ bởi KMS sang S3 Bucket.
* Kiểm tra ALB nhận diện thành công trạng thái `Healthy` ở cổng 80 (Frontend) và cổng 8080 (Backend).
![Trạng thái Target Health của Backend](/images/h48.png)
![Trạng thái Target Health của Frontend](/images/h49.png)

**2. Kiểm thử Tải giả lập và Giám sát CloudWatch (Thứ 3)**
* Truy cập ứng dụng thành công qua DNS của Application Load Balancer để kiểm thử các luồng nghiệp vụ trên trình duyệt.
![Web High-Concurrency Payment Gateway](/images/h82.png)
![Kiểm toán tài khoản](/images/h84.png)
![Giả lập kiểm thử](/images/h85.png)
* Kiểm tra CloudWatch Log Group `/ecs/pg-logs`. Bóc tách thành công các log khởi chạy của Spring Boot, ghi nhận kết nối tới PostgreSQL và Redis sidecar.
![Log Streams backend](/images/h86.png)
* Giám sát lượng requests qua ALB bằng metrics `RequestCount` (Sum, 1 minutes). Biểu đồ trực quan tăng vọt chứng minh lượng traffic từ công cụ kiểm thử.
![Metrics RequestCount](/images/h87.png)
* **Kết quả K6:** Hệ thống đương đầu thành công 100 VUs tạo 10.000 giao dịch trong 1 phút 50 giây (Tỷ lệ thành công 99.78%). Cơ chế khóa phân tán bảo toàn tính nhất quán (delta = 0.00).
![Kết quả toàn vẹn dữ liệu k6](/images/h88.png)
* Các cảm biến Alarm hoạt động nhạy bén: AlarmLow (`CPU < 63%`) và AlarmHigh (`CPU > 70%`) được trigger chuẩn xác phục vụ Auto Scaling.
![Trạng thái CloudWatch Alarms](/images/h89.png)

**3. Hoàn thiện Tài liệu Workshop 10 Phần (Thứ 4)**
* Soạn thảo chi tiết 10 bước thực hành của Workshop bằng từ ngữ tiếng Anh chuyên ngành chuẩn xác khớp với giao diện AWS Console hiện hành.
* Các phần hướng dẫn đầy đủ từ việc cấu hình VPC, Security Groups, IAM Roles, ALB, ECS Cluster đến thiết lập S3 Backup & Recovery, giúp người dùng cuối dễ dàng theo dõi và tái lập kiến trúc.

**4. Báo cáo Chuỗi Sự kiện FCJ Community Day (Thứ 5)**
* Đóng gói bài viết Event 1: Kiến trúc AI Agent trên AWS, Prompt Engineering, Token Economics.
* Hoàn thiện bài viết Event 2: Tảng băng trôi sự trì hoãn, pipeline GenAI có Output Validator.
* Hoàn thiện bài viết Event 3: Quản lý Session WebSocket qua DynamoDB, phân lớp Container Docker, mạng IDS bằng Học máy và 8 bước học DevOps.

**5. Tài liệu Báo cáo Kỹ thuật Blog (Thứ 6)**
* **Blog 1 (DevOps):** Giải pháp CI/CD tinh gọn, thiết lập mạng tự động, ALB, Auto Scaling với ECS Express Mode.
* **Blog 2 (Cloud Operations):** Phục hồi thảm họa bằng Velero, EKS Pod Identity, xử lý lỗi kẹt Pod.
* **Blog 3 (FinOps):** Quản trị lưu trữ vượt 90 ngày Console, hàm SQL Athena tối ưu phân tích chi phí Cloud.