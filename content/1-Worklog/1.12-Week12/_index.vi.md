---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Mục tiêu tuần 12:

* Triển khai bộ nhớ đệm (Caching) và các giải pháp nâng cao về kiểm soát truy cập sử dụng Redis nhằm tối ưu hóa hiệu năng, chống trùng lặp giao dịch và bảo vệ tài nguyên hệ thống.
* Thiết lập cơ chế giới hạn tần suất (Rate Limiting) phân tán dựa trên Redis tại API Gateway, áp dụng chính sách giới hạn linh hoạt cho từng người dùng thông qua định danh JWT.
* Giải quyết bài toán tranh chấp tài nguyên (Concurrency Control) và chống lặp giao dịch (Idempotency) bằng cơ chế khóa phân tán (Distributed Lock) và bộ lọc kiểm tra Idempotency Token sử dụng Redis.
* Dịch chuyển ứng dụng Payment Gateway Microservices lên hạ tầng đám mây AWS, xây dựng tài liệu hướng dẫn thực hành (Workshop) chi tiết và hoàn thiện bản đề xuất dự án (Proposal) tích hợp sơ đồ kiến trúc 3 lớp bảo mật.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 1 | - Nghiên cứu cơ chế Cache dữ liệu cần thiết bằng Redis:<br>&emsp; + Tìm hiểu lý thuyết về bộ nhớ đệm phân tán (Distributed Cache) và các chiến lược lưu trữ (Cache-Aside, Write-Through).<br>&emsp; + Thiết lập cấu hình Spring Boot Redis Starter để kết nối với cơ sở dữ liệu Redis. | 03/07/2026 | 03/07/2026 | <https://redis.io/docs/> |
| 2 | - Triển khai cơ chế giới hạn tần suất (Rate Limiting) phân tán:<br>&emsp; + Tìm hiểu và áp dụng Redis Rate Limiter sử dụng cấu trúc Token Bucket tại API Gateway.<br>&emsp; + Nghiên cứu giải pháp phân tích mã JWT để lấy thông tin định danh người dùng (User ID) làm khóa giới hạn tần suất (Key Resolver) cho từng Client. | 04/07/2026 | 04/07/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| 3 | - Triển khai Khóa phân tán (Distributed Lock) tại Payment Service:<br>&emsp; + Nghiên cứu thuật toán Redlock và cách triển khai Distributed Lock bằng Redis (sử dụng Spring Integration Redis hoặc Redisson).<br>&emsp; + Tích hợp khóa phân tán vào luồng thanh toán để ngăn chặn tranh chấp số dư tài khoản khi có nhiều luồng gọi đồng thời. | 05/07/2026 | 05/07/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| 4 | - Cấu hình cơ chế chống trùng lặp giao dịch (Idempotency):<br>&emsp; + Thiết kế bộ lọc Idempotency Filter tại API Gateway và kiểm tra token tại Payment Service.<br>&emsp; + Sử dụng Redis để lưu giữ trạng thái xử lý của các Idempotency Keys đi kèm thời gian hết hạn (TTL) phù hợp để tránh việc khách hàng bị trừ tiền 2 lần khi bấm nút thanh toán liên tiếp. | 06/07/2026 | 07/07/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| 5 | - Triển khai và kiểm thử hạ tầng ứng dụng lên đám mây AWS:<br>&emsp; + Đóng gói các Docker Images (Backend & Frontend) đẩy lên ECR và khởi chạy dịch vụ trên ECS Fargate.<br>&emsp; + Thiết lập kết nối cơ sở dữ liệu RDS PostgreSQL cô lập trong Private Subnet và nạp schema qua EC2 Bastion Host.<br>&emsp; + Cấu hình giải pháp xuất RDS Snapshot định kỳ sang Amazon S3 sử dụng KMS Key. | 08/07/2026 | 08/07/2026 | <https://calculator.aws/> |
| 6 | - Hoàn thiện tài liệu dự án và hướng dẫn thực hành:<br>&emsp; + Biên soạn 10 phần tài liệu hướng dẫn thực hành (Workshop) chi tiết từng bước nhấp chuột trên AWS Console.<br>&emsp; + Viết lại toàn bộ Bản đề xuất (Proposal) tích hợp sơ đồ kiến trúc Mermaid 3 lớp bảo mật và bảng tính toán chi phí vận hành chi tiết trên AWS. | 09/07/2026 | 10/07/2026 | [Bản đề xuất](file:///D:/aws/fcj-workshop-template/content/2-Proposal/_index.vi.md) |

### Kết quả đạt được tuần 12:

* **Tích hợp thành công cơ chế Cache dữ liệu bằng Redis:**
  * Giảm tải truy vấn trực tiếp đến RDS PostgreSQL đối với các thông tin tĩnh hoặc dữ liệu ít thay đổi (cấu hình cổng thanh toán, thông tin sản phẩm) bằng cách lưu trữ tạm thời trên Redis Cache.
  * Tối ưu hóa thời gian phản hồi (latency) của các API cốt lõi xuống dưới 50ms.

* **Triển khai thành công bộ lọc Rate Limiting phân tán theo JWT tại API Gateway:**
  * Xây dựng Key Resolver tự định nghĩa giải mã tiêu đề `Authorization` chứa JWT Token để trích xuất `userId` độc nhất.
  * Sử dụng Redis làm cơ sở dữ liệu lưu trữ số lượng tokens còn lại cho từng user, chặn đứng các yêu cầu vượt ngưỡng (mã lỗi 429) một cách chính xác trên toàn cụm instances chạy song song.

* **Giải quyết bài toán tranh chấp tài nguyên bằng Distributed Lock:**
  * Thiết lập thành công Distributed Lock bằng Redis trên Payment Service dựa trên cấu trúc khóa `payment_lock:{accountId}`.
  * Đảm bảo tính nhất quán dữ liệu số dư tài khoản ngân hàng, loại bỏ hoàn toàn lỗi chênh lệch số dư (Race Condition) khi có nhiều yêu cầu thanh toán đồng thời gửi tới cùng một ví/tài khoản.

* **Hoàn thiện giải pháp chống trùng lặp giao dịch (Idempotency):**
  * Tích hợp bộ lọc kiểm tra Idempotency Key gửi từ Client. Lưu trữ key này trên Redis dưới dạng cặp key-value kèm trạng thái xử lý (`PROCESSING`/`COMPLETED`) và đặt thời gian hết hạn (TTL: 10 phút).
  * Chặn đứng và trả về kết quả cũ đối với các request trùng lặp gửi lên liên tiếp trong thời gian ngắn, bảo vệ tính toàn vẹn cho luồng nghiệp vụ tài chính.

* **Triển khai hạ tầng thực chiến thành công lên AWS:**
  * Đóng gói mã nguồn Backend Gradle (gồm Java + Redis sidecar) và Frontend Nginx đẩy lên AWS ECR. Triển khai thành công lên ECS Fargate chạy an toàn bên trong các Private Subnets.
  
  ![Triển khai dịch vụ thành công trên ECS Fargate](/images/h47.png)

  * Khởi tạo thành công database RDS PostgreSQL cô lập hoàn toàn, kết nối thông suốt qua JDBC và nạp schema SQL thông qua cầu nối an toàn EC2 Bastion Host.
  * Truy cập ứng dụng thành công qua DNS của Application Load Balancer để kiểm thử các luồng nghiệp vụ.
  
  ![Giao diện NextGenPay chạy thực tế trên ALB DNS](/images/h69.png)

  * Thiết lập giải pháp khôi phục thảm họa: chụp RDS Snapshot thủ công và cấu hình IAM policy/role cho phép export dữ liệu nén bảo vệ bởi KMS Customer Managed Key sang S3 Bucket.

* **Hoàn thiện tài liệu hệ thống và báo cáo:**
  * Soạn thảo chi tiết 10 bước thực hành của Workshop bằng từ ngữ tiếng Anh chuyên ngành chuẩn xác khớp với AWS Console.
  * Viết mới hoàn toàn trang chủ Bản đề xuất (Proposal) tích hợp sơ đồ kiến trúc Mermaid 3 lớp bảo mật và bảng dự toán chi phí vận hành (~100 USD/tháng) giúp báo cáo thực tập đạt điểm đánh giá tối đa.
  * Thực hiện kiểm thử tải giả lập bằng script PowerShell và theo dõi lưu lượng cuộc gọi qua CloudWatch Metrics:

  ![Biểu đồ giám sát RequestCount thực tế trên CloudWatch](/images/h70.png)
