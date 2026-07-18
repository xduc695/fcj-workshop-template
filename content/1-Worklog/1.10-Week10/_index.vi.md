---
title: "Worklog Tuần 10"
date: 2026-06-22
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10:

* Tìm hiểu quy trình và thực hành triển khai hệ thống sao lưu, phục hồi thảm họa trên Amazon EKS bằng Velero.
* Tìm hiểu quy trình và thực hành triển khai hệ thống lưu trữ dữ liệu dung lượng EC2 dài hạn, phục vụ phân tích và tối ưu hóa chi phí (FinOps) bằng Amazon S3 và Amazon Athena.
* Nghiên cứu cơ chế API Gateway, giải pháp giới hạn tần suất (Rate Limiting) và nền tảng điều phối K8s.
* Thực hành cấu hình Resilience4j (Retry & Circuit Breaker) và API Gateway (LocalRateLimiter) bảo vệ giao tiếp Microservices.
* Triển khai bộ nhớ đệm (Caching) và các giải pháp nâng cao về kiểm soát truy cập sử dụng Redis nhằm tối ưu hóa hiệu năng.
* Thiết lập cơ chế giới hạn tần suất (Rate Limiting) phân tán dựa trên Redis tại API Gateway, áp dụng chính sách cho từng người dùng qua định danh JWT.
* Giải quyết bài toán tranh chấp tài nguyên (Concurrency Control) và chống lặp giao dịch (Idempotency) bằng cơ chế khóa phân tán (Distributed Lock) sử dụng Redis.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Thực hành cấu hình hệ thống sao lưu, phục hồi thảm họa (Disaster Recovery) trên Amazon EKS bằng Velero: <br> - **Thực hành:** <br>&emsp; + Khởi tạo Amazon S3 Bucket lưu trữ cấu hình cụm <br>&emsp; + Tạo IAM Policy, IAM Role và cấu hình EKS Pod Identity Association <br>&emsp; + Cài đặt Snapshot Controller add-on và thiết lập VolumeSnapshotClass <br>&emsp; + Triển khai Velero Server bằng Helm Chart kết hợp ClusterRole <br>&emsp; + Triển khai ứng dụng mẫu (Stateful App) gắn ổ đĩa gp3 trong namespace myprimary <br>&emsp; + Thực thi Velero Backup sao lưu toàn bộ tài nguyên <br>&emsp; + Áp dụng Velero Restore kết hợp namespaceMapping khôi phục sang myrestore <br>&emsp; + Kiểm tra luồng dữ liệu, xử lý lỗi CMD, lỗi Pod Pending và dọn dẹp tài nguyên. | 22/06/2026 | 22/06/2026 | <https://aws.amazon.com/vi/blogs/containers/back-up-and-restore-your-amazon-eks-cluster-resources-using-velero/> |
| Thứ 3 | - Thực hành cấu hình hệ thống lưu trữ dữ liệu dài hạn trên Amazon EC2 bằng Capacity Manager và Amazon Athena (FinOps): <br> - **Thực hành:** <br>&emsp; + Khởi tạo Amazon S3 Bucket tập trung dữ liệu <br>&emsp; + Tạo S3 Bucket Policy cấp quyền ghi nhận dữ liệu cho EC2 Capacity Manager <br>&emsp; + Thiết lập luồng xuất dữ liệu (Data Export) hàng giờ định dạng Parquet <br>&emsp; + Khởi tạo Database và Cấu hình External Table trên Athena (Chiếu phân vùng Partition Projection) <br>&emsp; + Thực thi SQL săn tìm ODCR có hiệu suất thấp <br>&emsp; + Truy vấn phân tích Peak Usage Patterns <br>&emsp; + Truy vấn cấp độ AZ ID xác định dung lượng trống <br>&emsp; + Kiểm tra luồng dữ liệu và dọn dẹp (Clean up) tài nguyên. | 23/06/2026 | 23/06/2026 | <https://aws.amazon.com/vi/blogs/compute/maximize-amazon-ec2-capacity-reservations-with-capacity-manager-data-exports/> |
| Thứ 4 | - Cấu hình chuỗi giải pháp chống chịu lỗi với Resilience4j, API Gateway và K8s: <br> - **Thực hành:** <br>&emsp; + Tích hợp dependency Resilience4j vào Payment Service. <br>&emsp; + Cấu hình Retry (max-attempts: 3) và khoảng thời gian chờ tăng dần. <br>&emsp; + Tích hợp @Retry và @CircuitBreaker vào AccountServiceClient. <br>&emsp; + Thiết lập hàm dự phòng paymentFallbackMethod khi Account Service lỗi. <br>&emsp; + Khởi tạo dịch vụ API Gateway sử dụng Spring Cloud Gateway WebFlux. <br>&emsp; + Thiết kế bộ lọc LocalRateLimiterGatewayFilterFactory (Token Bucket In-memory). <br>&emsp; + Bóc tách, dọn dẹp (Clean up) toàn bộ cấu hình Rate Limit cũ tại Account Service. <br>&emsp; + Chạy script kiểm thử PowerShell xác thực Rate Limiting và Circuit Breaker. | 24/06/2026 | 24/06/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| Thứ 5 | - Thực hành cơ chế Cache dữ liệu cần thiết và Rate Limiting bằng Redis:<br> - **Thực hành:** <br>&emsp; + Tìm hiểu bộ nhớ đệm phân tán (Distributed Cache) và các chiến lược (Cache-Aside, Write-Through).<br>&emsp; + Thiết lập cấu hình Spring Boot Redis Starter kết nối với Redis.<br>&emsp; + Áp dụng Redis Rate Limiter sử dụng cấu trúc Token Bucket tại API Gateway.<br>&emsp; + Phân tích mã JWT để lấy User ID làm khóa giới hạn tần suất cho từng Client. | 25/06/2026 | 25/06/2026 | <https://redis.io/docs/><br><https://github.com/LonggTran/high-concurrency-payment-gateway> |
| Thứ 6 | - Thực hành Khóa phân tán (Distributed Lock) và chống trùng lặp (Idempotency):<br> - **Thực hành:** <br>&emsp; + Triển khai Distributed Lock bằng Redisson tại Payment Service.<br>&emsp; + Tích hợp khóa phân tán vào luồng thanh toán ngăn chặn tranh chấp số dư.<br>&emsp; + Thiết kế Idempotency Filter tại API Gateway và kiểm tra token tại Payment Service.<br>&emsp; + Sử dụng Redis lưu giữ trạng thái xử lý Idempotency Keys đi kèm TTL tránh trừ tiền 2 lần. | 26/06/2026 | 26/06/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |

### Kết quả đạt được tuần 10:

**1. Sao lưu, Phục hồi thảm họa EKS với Velero (Thứ 2)**
* Cấu hình thành công Velero tự động đóng gói tài nguyên logic thành file nén lưu trên S3 Bucket. Kích hoạt Snapshot Controller chụp ảnh đĩa vật lý Amazon EBS Snapshots `gp3`.
* Xác minh trạng thái sao lưu hoàn thành xuất sắc qua Phase của Backup Custom Resource.
![Velero Backup Completed](/images/100.png)
* Sử dụng `namespaceMapping` dịch chuyển toàn bộ tài nguyên sang namespace mới. AWS tự động khởi tạo ổ đĩa `gp3` mới gắn vào Worker Node.
* Thiết lập EKS Pod Identity Association loại bỏ thông tin xác thực tĩnh, áp dụng ClusterRole chuẩn Least Privilege.
![EKS Pod Identity Association](/images/101.png)

**2. EC2 Capacity Manager & Athena FinOps (Thứ 3)**
* Tiến trình Capacity Manager tự động xuất dữ liệu hạ tầng (On-Demand, Spot, ODCR) hàng giờ thành file nén Parquet (Snappy) đẩy về S3 Bucket. Cấu hình S3 Bucket Policy thành công.
* Xác minh trạng thái trường `LatestDeliveryStatus` mang giá trị `delivered`.
![Capacity Manager Data Export Delivered](/images/102.png)
* Áp dụng Partition Projection cho External Table giúp Athena tự động nhận diện phân vùng mới.
* Sử dụng SQL nâng cao săn tìm ODCR lãng phí, bóc tách Peak Usage, định vị dung lượng trống AZ ID.
![Athena SQL Query Results](/images/103.png)

**3. API Gateway, Rate Limiting In-memory & Resilience4j (Thứ 4)**
* Tích hợp thành công bộ lọc CircuitBreaker và Retry trên Feign Client của Payment Service. Cấu hình `failureRateThreshold`, `slidingWindowSize` tối ưu chống ngắt mạch sai lệch.
* Triển khai API Gateway làm điểm trung chuyển bảo vệ kiến trúc Microservices. Tích hợp bộ lọc Token Bucket In-Memory chống DDoS hiệu quả.
* Dọn dẹp cấu hình Rate Limit cũ ở Account Service giúp mã nguồn chuẩn Clean Code (SRP). Thực hiện test PowerShell ngắt mạch chuẩn xác.

**4. Tích hợp cơ chế Cache và Rate Limiting phân tán JWT (Thứ 5)**
* Giảm tải truy vấn trực tiếp đến RDS PostgreSQL với các thông tin tĩnh (cấu hình cổng thanh toán) bằng Redis Cache. Tối ưu hóa latency của API lõi xuống dưới 50ms.
* Xây dựng Key Resolver tự định nghĩa giải mã tiêu đề `Authorization` chứa JWT Token để trích xuất `userId` độc nhất.
* Sử dụng Redis lưu trữ tokens còn lại, chặn đứng các yêu cầu vượt ngưỡng (mã lỗi 429) chuẩn xác trên cụm instances song song.

**5. Distributed Lock và Idempotency chống lặp giao dịch (Thứ 6)**
* Thiết lập Distributed Lock bằng Redis trên Payment Service dựa trên cấu trúc khóa `payment_lock:{accountId}`.
* Đảm bảo tính nhất quán dữ liệu số dư, loại bỏ hoàn toàn lỗi chênh lệch số dư (Race Condition) khi gửi nhiều lệnh thanh toán đồng thời.
* Tích hợp bộ lọc Idempotency Key gửi từ Client. Lưu key trên Redis kèm trạng thái (`PROCESSING`/`COMPLETED`) và TTL 10 phút. Trả về kết quả cũ với các request trùng lặp liên tiếp.