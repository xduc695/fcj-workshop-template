---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

* Tạo cơ sở dữ liệu, triển khai mô hình DTO, chuẩn hóa API Response và xây dựng cơ chế Global Exception Handling cho dự án High-Concurrency Payment Gateway.
* Nghiên cứu và triển khai giải pháp tối ưu hóa chi phí vận hành EC2 thông qua việc tự động hóa lịch trình bật/tắt instance bằng AWS Lambda.
* Nghiên cứu kiến trúc Serverless và thực hành xây dựng hệ thống xử lý ảnh tự động bằng AWS Lambda, thực hiện các thao tác CRUD dữ liệu trên Amazon DynamoDB.
* Nghiên cứu và thực hành triển khai ứng dụng Web Front-end kết nối với hệ thống Backend Serverless thông qua việc cấu hình Amazon API Gateway làm trung gian điều phối request.
* Nghiên cứu và thực hành sử dụng open-source framework AWS SAM để lập mô hình ứng dụng bằng cú pháp YAML, qua đó tự động hóa quy trình chuyển đổi sang CloudFormation.
* Nghiên cứu dịch vụ Amazon Cognito và thực hành tích hợp giải pháp quản lý người dùng, xác thực và ủy quyền truy cập.
* Nghiên cứu và thực hành triển khai giải pháp giám sát, kiểm thử và tối ưu hóa hệ thống Serverless bằng cách sử dụng Amazon CloudWatch kết hợp AWS X-Ray.
* Thiết kế và triển khai dịch vụ thanh toán (Payment Service) đảm bảo khả năng xử lý High Concurrency, tích hợp cơ chế Idempotency ngăn chặn double-spending.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Thiết kế cấu trúc dữ liệu và triển khai các thành phần cốt lõi cho dự án High-Concurrency Payment Gateway:<br>&emsp; + Database Schema (Thiết kế cấu trúc tối ưu)<br>&emsp; + DTO (Mô hình đối tượng chuẩn hóa)<br>&emsp; + API Response (Định nghĩa cấu trúc phản hồi)<br>&emsp; + Global Exception Handling (Quản lý ngoại lệ)<br>&emsp; + Performance Optimization (Tối ưu hiệu năng)<br> - Thiết kế và triển khai dịch vụ thanh toán (Payment Service) đảm bảo High Concurrency:<br>&emsp; + Tách biệt Transaction khỏi HTTP Call, tối ưu Connection Pool<br>&emsp; + Idempotency Mechanism (ngăn chặn double-spending)<br>&emsp; + Inter-service Error Handling (Bắt lỗi liên dịch vụ)<br>&emsp; + Data Consistency (Bảo đảm tính nhất quán dữ liệu) | 08/06/2026 | 08/06/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| Thứ 3 | - Nghiên cứu tối ưu hóa chi phí EC2 qua tự động hóa bật/tắt bằng AWS Lambda: <br> - **Thực hành:** <br>&emsp; + Tạo Tag cho EC2 Instance <br>&emsp; + Tạo Role cho Lambda Function <br> &emsp; + Tạo Lambda Function thực hiện chức năng Stop instances <br> &emsp; + Tạo Lambda Function thực hiện chức năng Start instances<br> &emsp; + Kiểm tra kết quả tối ưu chi phí<br> - Nghiên cứu kiến trúc Serverless, thực hành hệ thống xử lý ảnh và CRUD DynamoDB: <br> - **Thực hành:** <br>&emsp; + Tạo Lambda Function Xử Lý Ảnh <br>&emsp; + Tạo S3 Bucket <br> &emsp; + Tạo IAM Policy và Kiểm tra Lambda Function <br>&emsp; + Tạo và Quản lý Bảng DynamoDB <br> &emsp; + Tạo Lambda Function Ghi dữ liệu vào DynamoDB | 09/06/2026 | 09/06/2026 | <https://000022.awsstudygroup.com/><br><https://000078.awsstudygroup.com/> |
| Thứ 4 | - Thực hành triển khai Web Front-end kết nối Backend Serverless qua API Gateway và AWS SAM: <br> - **Thực hành:** <br>&emsp; + Triển khai host front-end với S3 Static website hosting (dựa trên SAM) <br>&emsp; + Tạo bảng DynamoDB <br>&emsp; + Triển khai Lambda function ghi/đọc/xóa dữ liệu và chỉnh ảnh (dựa trên SAM) <br>&emsp; + Thiết lập API Gateway tương tác với Lambda function <br>&emsp; + Tạo GET/POST/DELETE API <br>&emsp; + Cài đặt và kích hoạt CORS <br>&emsp; + Kiểm tra API với Postman và Front-end | 10/06/2026 | 10/06/2026 | <https://000079.awsstudygroup.com/><br><https://000080.awsstudygroup.com/> |
| Thứ 5 | - Nghiên cứu Amazon Cognito và tích hợp xác thực ủy quyền an toàn cho Web Front-end: <br> - **Thực hành:** <br>&emsp; + Tạo User Pool <br>&emsp; + Tạo API và hàm Lambda để xử lý yêu cầu đăng ký và đăng nhập trên SAM<br>&emsp; + Thực hiện đăng ký và đăng nhập trên web để Kiểm tra front-end | 11/06/2026 | 11/06/2026 | <https://000081.awsstudygroup.com/> |
| Thứ 6 | - Nghiên cứu giải pháp giám sát, kiểm thử và tối ưu Serverless bằng CloudWatch và X-Ray: <br> - **Thực hành:** <br>&emsp; + Gỡ lỗi với nhật ký CloudWatch <br>&emsp; + Tạo số liệu tùy chỉnh với CloudWatch metric <br>&emsp; + Tạo cảnh báo với CloudWatch Alarm  <br>&emsp; + Theo dõi request của hàm Lambda với X-ray | 12/06/2026 | 12/06/2026 | <https://000085.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:

**1. Code Kiến trúc High-Concurrency Payment Gateway (Thứ 2)**
* Thiết kế cấu trúc dữ liệu và khởi tạo cơ sở dữ liệu (Database Schema) tối ưu, thiết lập chính xác khóa chính, khóa ngoại, ràng buộc (Constraints) bảo toàn tính toàn vẹn.
* Triển khai mô hình đối tượng DTO và định nghĩa Base Response cấu trúc JSON thống nhất chuẩn hóa dữ liệu đầu ra và HTTP Status Code.
* Xây dựng cơ chế Global Exception Handling tập trung (`ControllerAdvice`) định dạng chuẩn hóa thông báo lỗi, ẩn thông tin nhạy cảm.
* Tối ưu xử lý chịu tải cao và Connection Pool: Tách biệt logic Transaction khỏi luồng gọi HTTP Call, giải phóng kết nối DB nhanh chóng ngăn chặn nghẽn.
* Triển khai Idempotency Mechanism chống trùng lặp, tích hợp `Unique Constraint` ngăn chặn double-spending. Xây dựng cơ chế bắt lỗi liên dịch vụ, cấu hình HTTP Timeout chặt chẽ.

**2. EC2 Auto-Stop & Xử lý ảnh Serverless (Thứ 3)**
* Tự động hóa lịch trình EC2: Gắn Tag `environment_auto: true`, tạo IAM Role `dc-common-lambda-role`, lập trình 2 hàm Lambda (`auto-start`, `auto-stop`) bằng Python (Boto3) kết nối Slack. Cấu hình EventBridge Rules.
* Kết quả: EC2 tự động chuyển trạng thái, kênh Slack nhận thông báo thời gian thực báo cáo chính xác ID instance.
![EC2 Stopped](/images/80.png)
![Slack message](/images/81.png)
* Khởi tạo 2 S3 Buckets, cấu hình Event Trigger. Triển khai Lambda `resize-image` tự động thay đổi kích thước ảnh và đồng bộ sang bucket đích.
![S3 Resize Successful](/images/82.png)
* Lập trình hàm Lambda `book_create` ghi dữ liệu `put_item` vào bảng DynamoDB `Books` On-demand. Test Event thành công.
![DynamoDB Explore Items](/images/83.png)

**3. API Gateway, CORS & Tự động hóa SAM (Thứ 4)**
* Cấu hình S3 Static Website Hosting phân phối Front-end công khai. Khởi tạo REST API Gateway (Lambda Proxy Integration) hỗ trợ dữ liệu nhị phân `multipart/form-data`, kích hoạt CORS.
* Kiểm thử Postman trả về mã 200 OK, Front-end liên kết endpoint hiển thị đầy đủ tính năng CRUD đồng bộ.
![Postman API Test Result](/images/84.png)
![Front-end Interface Verification](/images/85.png)
* Tự động hóa hạ tầng bằng AWS SAM YAML (`template.yaml`). Đồng bộ qua CloudFormation lệnh `sam deploy`, đóng gói 4 hàm Lambda (`books_list`, `book_create`, `book_delete`, `resize_image`).
![Postman Integration Verification](/images/86.png)
![Front-end System Validation](/images/87.png)

**4. Xác thực Ủy quyền Amazon Cognito (Thứ 5)**
* Khởi tạo User Pool định danh bằng Email. Cấu hình App Client luồng `ALLOW_USER_PASSWORD_AUTH`. Lập trình 3 hàm Lambda (`Register`, `Confirm`, `Login`). Đồng bộ SAM tự động hóa.
* Kiểm thử Front-end: Gửi mã xác nhận Đăng ký về email và đăng nhập tiếp nhận Token bảo mật chính xác.
![Cognito Verification Mail](/images/88.png)
![Front-end Authentication Success](/images/89.png)

**5. Giám sát & Phân tích với CloudWatch, X-Ray (Thứ 6)**
* Khai thác Log Streams bóc tách lỗi runtime (như lỗi cấu hình sai tên bảng). Định nghĩa số liệu tùy chỉnh đẩy qua phương thức `put_metric_data`.
![CloudWatch Log Debugging](/images/90.png)
* Thiết lập CloudWatch Alarm và Amazon SNS gửi email cảnh báo khi môi trường `staging` vượt ngưỡng lỗi kết nối DynamoDB.
* Kích hoạt AWS X-Ray (thư viện `aws_xray_sdk`), vẽ bản đồ kiến trúc luồng gọi theo dõi chi tiết độ trễ của các request tương tác qua lại.
![AWS X-Ray Trace Service Map & Timeline](/images/91.png)