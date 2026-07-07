---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

* Tạo cơ sở dữ liệu, triển khai mô hình DTO, chuẩn hóa API Response và xây dựng cơ chế Global Exception Handling cho dự án Microservice hệ thống ngân hàng chịu tải cao
* Nghiên cứu và triển khai giải pháp tối ưu hóa chi phí vận hành EC2 thông qua việc tự động hóa lịch trình bật/tắt instance bằng AWS Lambda và áp dụng giải pháp dài hạn Savings Plans cho các máy chủ hoạt động liên tục.
* Nghiên cứu kiến trúc Serverless và thực hành xây dựng hệ thống xử lý ảnh tự động bằng AWS Lambda, thực hiện các thao tác CRUD dữ liệu trên Amazon DynamoDB, đồng thời áp dụng các tiêu chuẩn tối ưu bảo mật, giám sát và xử lý sự cố.
* Nghiên cứu và thực hành triển khai ứng dụng Web Front-end kết nối với hệ thống Backend Serverless thông qua việc cấu hình Amazon API Gateway làm trung gian điều phối request đến các hàm AWS Lambda, đồng thời thực hiện kiểm thử toàn diện bằng cả Postman và giao diện người dùng.
* Nghiên cứu và thực hành sử dụng open-source framework AWS SAM để lập mô hình ứng dụng bằng cú pháp YAML, qua đó tự động hóa quy trình chuyển đổi sang CloudFormation để tái triển khai nhanh chóng toàn bộ kiến trúc Serverless gồm Web Front-end, API Gateway và Lambda function.
* Nghiên cứu dịch vụ Amazon Cognito và thực hành tích hợp giải pháp quản lý người dùng, xác thực và ủy quyền truy cập an toàn cho ứng dụng Web Front-end kết nối qua API Gateway và AWS Lambda.
* Nghiên cứu và thực hành triển khai giải pháp giám sát, kiểm thử và tối ưu hóa hệ thống Serverless bằng cách sử dụng Amazon CloudWatch kết hợp AWS X-Ray nhằm phân tích lược đồ cuộc gọi và xử lý tận gốc các sự cố hiệu suất.
* Thiết kế và triển khai dịch vụ thanh toán (Payment Service) đảm bảo khả năng xử lý High Concurrency, tích hợp cơ chế Idempotency ngăn chặn double-spending, xây dựng quy trình Inter-service Error Handling chặt chẽ và tối ưu hóa Connection Pool nhằm bảo đảm tính nhất quán dữ liệu (Data Consistency) tuyệt đối cho hệ thống ngân hàng.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Thiết kế cấu trúc dữ liệu và triển khai các thành phần cốt lõi cho dự án Microservice ngân hàng chịu tải cao:<br>&emsp; + Database Schema (Thiết kế và khởi tạo cấu trúc tối ưu cho các dịch vụ)<br>&emsp; + DTO (Triển khai mô hình đối tượng chuẩn hóa và bảo mật luồng dữ liệu giữa các layer)<br>&emsp; + API Response (Định nghĩa và cấu hình cấu trúc phản hồi dữ liệu thống nhất)<br>&emsp; + Global Exception Handling (Xây dựng cơ chế quản lý ngoại lệ và trả về mã lỗi chuẩn hóa)<br>&emsp; + Performance Optimization (Áp dụng các giải pháp kỹ thuật như Indexing để tối ưu hiệu năng)                                                                                             | 05/06/2026   | 05/06/2026      |
| 2   | - Nghiên cứu và triển khai giải pháp tối ưu hóa chi phí vận hành EC2 thông qua việc tự động hóa lịch trình bật/tắt instance bằng AWS Lambda và áp dụng giải pháp dài hạn Savings Plans cho các máy chủ hoạt động liên tục: <br> - **Thực hành:** <br>&emsp; + Tạo Tag cho EC2 Instance <br>&emsp; + Tạo Role cho Lambda Function <br> &emsp; + Tạo Lambda Function thực hiện chức năng Stop instances <br> &emsp; + Tạo Lambda Function thực hiện chức năng Start instances<br> &emsp; + Kiểm tra kết quả tối ưu chi phí cho hệ thống <br> - Nghiên cứu kiến trúc Serverless và thực hành xây dựng hệ thống xử lý ảnh tự động bằng AWS Lambda, thực hiện các thao tác CRUD dữ liệu trên Amazon DynamoDB, đồng thời áp dụng các tiêu chuẩn tối ưu bảo mật, giám sát và xử lý sự cố: <br> - **Thực hành:** <br>&emsp; + Tạo Lambda Function Xử Lý Ảnh <br>&emsp; + Tạo S3 Bucket <br> &emsp; + Tạo IAM Policy và Kiểm tra hoạt động của Lambda Function <br>&emsp; + Tạo và Quản lý Bảng trong AWS DynamoDB <br> &emsp; + Tạo Lambda Function để Ghi dữ liệu vào DynamoDB                                   | 06/06/2026   | 06/06/2026      | <https://000022.awsstudygroup.com/><br><https://000078.awsstudygroup.com/> |
| 3   | - Nghiên cứu và thực hành triển khai ứng dụng Web Front-end kết nối với hệ thống Backend Serverless thông qua việc cấu hình Amazon API Gateway làm trung gian điều phối request đến các hàm AWS Lambda, đồng thời thực hiện kiểm thử toàn diện bằng cả Postman và giao diện người dùng: <br> - **Thực hành:** <br>&emsp; + Triển khai host front-end với S3 Static website hosting <br>&emsp; + Tạo bảng trong DynamoDB <br> &emsp; + Triển khai Lambda function ghi/đọc/xóa dữ liệu <br>&emsp; + Thiết lập API Gateway tương tác với các Lambda function đã tạo <br>&emsp; + Tạo các method <br>&emsp; + Cài đặt và kích hoạt CORS <br> &emsp; + Kiểm tra API với Postman <br>&emsp; + Kiểm tra API với front-end | 07/06/2026   | 07/06/2026      | <https://000079.awsstudygroup.com/> |
| 4   | - Nghiên cứu và thực hành sử dụng open-source framework AWS SAM để lập mô hình ứng dụng bằng cú pháp YAML, qua đó tự động hóa quy trình chuyển đổi sang CloudFormation để tái triển khai nhanh chóng toàn bộ kiến trúc Serverless gồm Web Front-end, API Gateway và Lambda function: <br> - **Thực hành:** <br>&emsp; + Triển khai host front-end với S3 Static website hosting dựa trên AWS SAM <br>&emsp; + Tạo bảng trong DynamoDB với AWS SAM <br>&emsp; + Triển khai Lambda function ghi/đọc/xóa dữ liệu và chỉnh ảnh dựa trên AWS SAM <br>&emsp; + Thiết lập API Gateway tương tác với các Lambda function đã tạo trên SAM <br>&emsp; + Tạo GET/POST/DELETE API trên SAM <br>&emsp; + Kiểm tra API với Postman <br>&emsp; + Kiểm tra API với front-end                   | 08/06/2026   | 08/06/2026      | <https://000080.awsstudygroup.com/> |
| 5   | - Nghiên cứu dịch vụ Amazon Cognito và thực hành tích hợp giải pháp quản lý người dùng, xác thực và ủy quyền truy cập an toàn cho ứng dụng Web Front-end kết nối qua API Gateway và AWS Lambda: <br> - **Thực hành:** <br>&emsp; + Tạo User Pool <br>&emsp; + Tạo API và hàm Lambda để xử lý yêu cầu đăng ký và đăng nhập người dùng trên SAM<br>&emsp; + Tiến hành thực hiện đăng ký và đăng nhập trên web để Kiểm tra front-end <br> - Nghiên cứu và thực hành triển khai giải pháp giám sát, kiểm thử và tối ưu hóa hệ thống Serverless bằng cách sử dụng Amazon CloudWatch kết hợp AWS X-Ray nhằm phân tích lược đồ cuộc gọi và xử lý tận gốc các sự cố hiệu suất: <br> - **Thực hành:** <br>&emsp; + Gỡ lỗi với nhật ký CloudWatch <br>&emsp; + Tạo số liệu tùy chỉnh với CloudWatch metric <br>&emsp; + Tạo cảnh báo với CloudWatch Alarm  <br>&emsp; + Theo dõi request của hàm Lambda với X-ray                                                                                | 09/06/2026   | 09/06/2026      | <https://000081.awsstudygroup.com/><br><https://000085.awsstudygroup.com/> |
| 6   | - Thiết kế và triển khai dịch vụ thanh toán (Payment Service) đảm bảo khả năng xử lý High Concurrency, tích hợp cơ chế Idempotency ngăn chặn double-spending, xây dựng quy trình Inter-service Error Handling chặt chẽ và tối ưu hóa Connection Pool nhằm bảo đảm tính nhất quán dữ liệu (Data Consistency) tuyệt đối cho hệ thống ngân hàng:<br>&emsp; + High Concurrency & Connection Pool (Tách biệt Transaction khỏi HTTP Call, cấu hình Timeout và tối ưu hóa vòng đời kết nối DB)<br>&emsp; + Idempotency Mechanism (Thiết kế Key giao dịch duy nhất kết hợp Database Unique Constraint để ngăn chặn double-spending)<br>&emsp; + Inter-service Error Handling (Xây dựng cơ chế bắt lỗi liên dịch vụ, cấu hình HTTP Connect/Read Timeout và ghi nhận trạng thái lỗi chi tiết)<br>&emsp; + Data Consistency (Áp dụng Database-level Constraint và Transaction Isolation để bảo đảm tính nhất quán dữ liệu giao dịch)<br>&emsp; + ...                                                                                            | 10/06/2026   | 10/06/2026      |  <https://github.com/LonggTran/high-concurrency-payment-gateway>|
### Kết quả đạt được tuần 8:

* Thiết kế cấu trúc dữ liệu và khởi tạo cơ sở dữ liệu (Database Schema) tối ưu:
  * Khởi tạo thành công cấu trúc cơ sở dữ liệu cho các dịch vụ ngân hàng, phân chia các bảng logic rõ ràng đảm bảo tính độc lập dữ liệu giữa các Microservices.
  * Thiết lập chính xác hệ thống khóa chính, khóa ngoại, các ràng buộc dữ liệu (Constraints) nghiêm ngặt để bảo toàn tính toàn vẹn dữ liệu.

* Triển khai mô hình đối tượng DTO và chuẩn hóa API Response:
  * Lập trình hoàn chỉnh các lớp đối tượng DTO (Data Transfer Object) để đóng gói dữ liệu, che giấu các thông tin nhạy cảm của tài khoản và bảo mật luồng dữ liệu truyền tải giữa các layer.
  * Định nghĩa và áp dụng thành công lớp Base Response cấu trúc JSON thống nhất cho toàn bộ hệ thống, giúp chuẩn hóa dữ liệu đầu ra và các mã trạng thái HTTP Status Code cho các endpoint.

* Xây dựng cơ chế Global Exception Handling tập trung:
  * Triển khai bộ cấu hình xử lý lỗi tập trung (sử dụng ControllerAdvice và ExceptionHandler) để tự động bắt tất cả các ngoại lệ phát sinh trong runtime.
  * Định dạng và chuẩn hóa thành công các thông báo lỗi trả về cho client, ẩn đi các thông tin stack trace nhạy cảm của hệ thống ngân hàng khi xảy ra sự cố.

* Áp dụng giải pháp Performance Optimization để tối ưu hiệu năng:
  * Cấu hình và thiết lập hệ thống Index phù hợp trên các trường dữ liệu hay truy vấn của cơ sở dữ liệu nhằm tăng tốc độ tìm kiếm.

* Tự động hóa lịch trình hoạt động và quản lý định danh tài nguyên EC2:
  * Hoàn thành gắn Tag `environment_auto: true` trên EC2 instance, phục vụ chính xác cho bộ lọc của Lambda.
  * Khởi tạo thành công IAM Role (`dc-common-lambda-role`) cấp quyền `AmazonEC2FullAccess` và `CloudWatchFullAccess` cho Lambda.

* Triển khai code Lambda Function và cấu hình kích hoạt tự động:
  * Hoàn thành lập trình 2 hàm Lambda (`auto-start`, `auto-stop`) bằng Python sử dụng thư viện Boto3 và kết nối thành công Slack Webhook.
  * Cấu hình thành công 2 Rules trên EventBridge để tự động kích hoạt các hàm Lambda theo đúng lịch trình định sẵn.

* Kết quả thực nghiệm hệ thống:
  * Hệ thống tự động chuyển trạng thái EC2 thành công giữa `Running` và `Stopped` mỗi khi Lambda được kích hoạt.
  * Kênh Slack nhận thông báo thời gian thực báo cáo chính xác ID của instance vừa được xử lý.
  ![EC2 Stopped](/images/80.png)
  ![Slack message](/images/81.png)

* Nghiên cứu kiến trúc Serverless và cấu hình lưu trữ với Amazon S3:
  * Nắm vững nguyên lý hoạt động của kiến trúc Serverless và cơ chế Event-driven giữa S3 và Lambda.
  * Khởi tạo thành công 2 S3 Buckets (chứa ảnh gốc và ảnh nén) cùng cấu hình Event Trigger để tự động kích hoạt hàm xử lý ảnh.

* Triển khai Lambda Function xử lý ảnh tự động (Node.js):
  * Cấu hình thành công hàm Lambda `resize-image` kết hợp IAM Policy cấp quyền thao tác dữ liệu (`GetObject`, `DeleteObject`, `PutObject`) trên S3.
  * Thực nghiệm thành công chu trình tự động thay đổi kích thước ảnh và đồng bộ hóa sang bucket đích ngay khi upload.
  ![S3 Resize Successful](/images/82.png)

* Thiết lập cơ sở dữ liệu và triển khai Lambda ghi dữ liệu vào DynamoDB (Python):
  * Khởi tạo thành công bảng NoSQL `Books` (Partition Key: `id`) chạy chế độ tối ưu chi phí On-demand trên DynamoDB.
  * Lập trình và phân quyền thành công hàm Lambda `book_create` sử dụng thư viện Boto3 để thực hiện thao tác ghi dữ liệu (`put_item`).
  * Thực hiện Test Event thành công, dữ liệu JSON được cập nhật và hiển thị chuẩn xác trong bảng DynamoDB.
  ![DynamoDB Explore Items](/images/83.png)

* Triển khai lưu trữ Front-end và cơ sở dữ liệu DynamoDB:
  * Cấu hình thành công S3 Static Website Hosting và Bucket Policy để phân phối mã nguồn Front-end công khai.
  * Khởi tạo thành công bảng NoSQL `Books` kết hợp Local Secondary Index (`name-index`) và import hoàn tất dữ liệu mẫu bằng AWS CLI.

* Lập trình bộ ba hàm AWS Lambda (Python):
  * Cấu hình hoàn chỉnh các hàm Lambda điều phối dữ liệu gồm: `book_create` (ghi dữ liệu/tải ảnh), `books_list` (đọc/quét dữ liệu), và `book_delete` (xóa bản ghi/xóa ảnh).
  * Phân quyền thành công IAM Role cấp đầy đủ quyền thao tác dữ liệu trên S3 và DynamoDB cho các hàm thực thi.

* Thiết lập Amazon API Gateway làm trung gian điều phối:
  * Khởi tạo thành công REST API kết hợp cơ chế Lambda Proxy Integration cho các phương thức `GET`, `POST` (tại `/books`) và `DELETE` (tại `/{id}`).
  * Kích hoạt thành công cấu hình CORS và cấu hình hỗ trợ dữ liệu nhị phân `multipart/form-data` để tiếp nhận file từ client.

* Kiểm thử tích hợp toàn diện hệ thống Serverless:
  * Xác thực các API hoạt động chính xác qua Postman và kết nối thành công URL endpoint vào mã nguồn Front-end.
  * Nghiệm thu thực tế trên giao diện người dùng: hệ thống hiển thị danh sách, tải ảnh, thêm mới và xóa dữ liệu đồng bộ thời gian thực.
  ![Postman API Test Result](/images/84.png)
  ![Front-end Interface Verification](/images/85.png)

  * Tự động hóa hạ tầng (IaC) bằng cú pháp AWS SAM YAML:
  * Khởi tạo thành công cấu trúc tệp `template.yaml` để quản lý tập trung và lập mô hình toàn bộ tài nguyên hệ thống bằng mã nguồn.
  * Tự động hóa quy trình dịch chuyển và đồng bộ tài nguyên lên AWS thông qua CloudFormation ChangeSets bằng lệnh `sam deploy`.

* Định nghĩa tài nguyên S3 và DynamoDB bằng code:
  * Cấu hình thành công S3 Bucket có bật tính năng `WebsiteConfiguration` và `BucketPolicy` để phân phối Web tĩnh công khai.
  * Khai báo thành công bảng `BooksTable` ở chế độ On-demand (`PAY_PER_REQUEST`) kết hợp Local Secondary Index (`name-index`) trực tiếp trong template.

* Triển khai bộ bốn hàm AWS Lambda và phân quyền:
  * Đóng gói và cấu hình thành công môi trường thực thi cho 4 hàm Lambda xử lý nghiệp vụ (`books_list`, `book_create`, `book_delete`, `resize_image`).
  * Khai báo khối `Policies` và `Events` trong SAM để tự động sinh IAM Role cấp quyền và thiết lập S3 Event Trigger cho hàm xử lý ảnh.

* Đồng bộ hóa kiến trúc REST API Gateway:
  * Lập mô hình thành công tài nguyên `RestApi`, các Resource (`/books`, `/{id}`) và kích hoạt cấu hình hỗ trợ dữ liệu nhị phân `multipart/form-data`.
  * Cấu hình thành công tích hợp `AWS_PROXY` kết hợp thiết lập các tham số Header phản hồi để kích hoạt CORS cho các phương thức API.

* Kiểm thử và nghiệm thu tích hợp hệ thống:
  * Xác thực các API hoạt động chính xác thông qua kiểm thử độc lập trên Postman với mã phản hồi `200 OK`.
  ![Postman Integration Verification](/images/86.png)
  * Biên dịch mã nguồn Front-end liên kết với endpoint mới trên S3, hoàn thành nghiệm thu thực tế luồng tính năng CRUD mượt mà trên giao diện.
  ![Front-end System Validation](/images/87.png)

* Khởi tạo và cấu hình Amazon Cognito User Pool:
  * Khởi tạo thành công User Pool (`cognito-fcj-book-shop`) sử dụng cơ chế định danh bằng Email để quản lý người dùng.
  * Cấu hình thành công App Client, thiết lập luồng xác thực `ALLOW_USER_PASSWORD_AUTH` và trích xuất chính xác cặp khóa `Client ID / Client Secret`.

* Triển khai bộ ba hàm AWS Lambda điều phối xác thực (Python):
  * Lập trình và phân quyền thành công 3 hàm Lambda xử lý logic: `Register` (đăng ký người dùng với `secret_hash`), `Confirm` (xác thực mã kích hoạt từ Mail), và `Login` (đăng nhập và cấp bộ ba mã Token bảo mật).

* Đồng bộ kiến trúc endpoint API Gateway qua AWS SAM:
  * Khai báo thành công các Resource API mới (`/register`, `/confirm_user`, `/login`) tích hợp cơ chế `AWS_PROXY` (POST) và cấu hình phương thức `OPTIONS` để kích hoạt CORS toàn diện.
  * Cập nhật thành công khối `BookApiDeployment` giúp tự động hóa quy trình đóng gói và triển khai đồng bộ toàn bộ hạ tầng bảo mật.

* Kiểm thử và nghiệm thu tính năng xác thực trên Front-end:
  * Xác thực quy trình gửi mã xác nhận về hòm thư điện tử của người dùng ngay sau khi thực hiện thao tác Đăng ký thành công trên giao diện.
  ![Cognito Verification Mail](/images/88.png)
  * Nghiệm thu luồng Đăng nhập thành công, hệ thống tiếp nhận Token bảo mật chính xác và tự động hiển thị đầy đủ các tính năng quản trị (`Create new book`, `Management`).
  ![Front-end Authentication Success](/images/89.png)

  * Quản lý nhật ký và gỡ lỗi hệ thống (Debugging) với CloudWatch Logs:
  * Khai thác thành công công cụ **Log Streams** để bóc tách toàn bộ dữ liệu log runtime của hàm Lambda, giúp khoanh vùng và xử lý triệt để lỗi cấu hình sai tên bảng (`TableName='Book'`) dẫn đến lỗi `Internal Server Error`.
  ![CloudWatch Log Debugging](/images/90.png)

* Định nghĩa số liệu tùy chỉnh (Custom Metric) qua CloudWatch Metrics:
  * Lập trình nhúng thành công phương thức `put_metric_data` bằng thư viện Boto3 để tự động đẩy chỉ số giám sát lỗi kết nối (`FailedConnectToDynamoDB`) về không gian tên tùy chỉnh (`BooksList_Lambda`).
  * Cấu hình và phân quyền thành công IAM Role (`BooksListRolePolicy0`) với chính sách `cloudwatch:PutMetricData` để cấp quyền ghi chỉ số an toàn từ Lambda lên hệ thống CloudWatch.

* Thiết lập hệ thống cảnh báo tự động với CloudWatch Alarm và Amazon SNS:
  * Khởi tạo thành công cảnh báo `fcj-fail-connect-to-dynamodb-alarm` dựa trên điều kiện tích lũy mã lỗi (`Sum >= 2`) trong môi trường `staging`.
  * Liên kết thành công Alarm với **Amazon SNS Topic** (`fcj_cloudwatch_alarm_topic`) giúp tự động kích hoạt tiến trình gửi email cảnh báo thời gian thực ngay khi hệ thống vượt ngưỡng lỗi quy định.

* Giám sát và phân tích vết cuộc gọi (Distributed Tracing) bằng AWS X-Ray:
  * Kích hoạt thành công tính năng **Lambda service traces** trên bảng điều khiển để bóc tách chi tiết thời gian xử lý của các phân đoạn vòng đời Lambda (`Initialization`, `Invocation`, `Overhead`).
  * Tích hợp thành công thư viện mã nguồn mở `aws_xray_sdk` bằng lệnh `patch_all()` trong Python, cho phép X-Ray tự động vẽ bản đồ kiến trúc luồng gọi (Service Map) và theo dõi chi tiết độ trễ của các request tương tác qua lại giữa Lambda, API Gateway và cơ sở dữ liệu DynamoDB.
  ![AWS X-Ray Trace Service Map & Timeline](/images/91.png)

* Tối ưu xử lý chịu tải cao và sử dụng Connection Pool:
  * Tách biệt thành công logic Transaction khỏi luồng gọi HTTP Call, giải phóng kết nối DB nhanh chóng và ngăn chặn nghẽn hệ thống khi tải cao.
  * Tối ưu hóa vòng đời sử dụng kết nối DB bằng cơ chế tách biệt Transaction (TransactionTemplate), giải phóng connection về pool nhanh chóng và nâng cao năng lực xử lý đồng thời cho dịch vụ thanh toán.

* Triển khai cơ chế Idempotency Mechanism chống trùng lặp:
  * Thiết kế và áp dụng thành công Idempotency Key duy nhất cho từng yêu cầu thanh toán từ Client.
  * Tích hợp thành công ràng buộc duy nhất (`Unique Constraint`) ở mức Database, ngăn chặn triệt để tình trạng xử lý trùng và lỗi double-spending.

* Xử lý lỗi liên dịch vụ (Inter-service Error Handling):
  * Xây dựng hoàn chỉnh cơ chế bắt lỗi liên dịch vụ, giúp cô lập lỗi cục bộ và tránh gây sập hệ thống dây chuyền giữa các Microservices.
  * Cấu hình chính xác HTTP Connect/Read Timeout và triển khai hệ thống ghi log trạng thái lỗi chi tiết phục vụ tra soát giao dịch.

* Bảo đảm tính nhất quán dữ liệu (Data Consistency):
  * Áp dụng thành công các cấp độ cô lập giao dịch (Transaction Isolation) và các ràng buộc dữ liệu nghiêm ngặt mức Database-level.
  * Đảm bảo tính nhất quán dữ liệu tuyệt đối giữa số dư tài khoản và lịch sử giao dịch ngân hàng ngay cả khi xảy ra sự cố gián đoạn mạng.