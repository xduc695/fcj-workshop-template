---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu tuần 6:

* Tìm hiểu các dịch vụ hỗ trợ triển khai Front-end, mạng phân phối nội dung và bảo mật ứng dụng web.
* Tìm hiểu kiến trúc tính toán phi máy chủ (Serverless) và cách quản lý, định tuyến giao tiếp API.
* Tìm hiểu các nền tảng điều phối và quản lý hệ thống Container (Docker/Kubernetes) trên đám mây.
* Tìm hiểu các giải pháp xử lý luồng dữ liệu thời gian thực (Streaming) và hàng đợi thông điệp bất đồng bộ.
* Tìm hiểu quy trình tích hợp dữ liệu (ETL) và nền tảng xử lý dữ liệu khổng lồ (Big Data).
* Tìm hiểu giải pháp Kho dữ liệu (Data Warehouse), công cụ trực quan hóa (BI) và nền tảng AI tạo sinh.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Tìm hiểu về các dịch vụ Front-end và bảo mật ứng dụng web: <br>&emsp; + AWS Amplify <br>&emsp; + Amazon CloudFront <br>&emsp; + AWS WAF                                                                                             | 22/05/2025   | 22/05/2025    | <https://cloudjourney.awsstudygroup.com/> |
| 2   | - Tìm hiểu về kiến trúc Serverless và định tuyến giao tiếp API: <br>&emsp; + AWS API Gateway <br>&emsp; + AWS Lambda                                            | 23/05/2025   | 23/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tìm hiểu về các nền tảng điều phối và quản lý Container: <br>&emsp; + Amazon ECS <br>&emsp; + Amazon EKS | 24/05/2025   | 24/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu về dịch vụ xử lý luồng dữ liệu thời gian thực (Real-time Streaming): <br>&emsp; + Amazon Kinesis <br>&emsp; + Amazon MSK (Apache Kafka)                                                                                | 25/05/2025   | 25/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu về quy trình tích hợp dữ liệu và nền tảng Big Data: <br>&emsp; + AWS Glue <br>&emsp; + Amazon EMR                                                                               | 26/05/2025   | 26/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu về Kho dữ liệu, phân tích BI và AI tạo sinh: <br>&emsp; + Amazon Redshift <br>&emsp; + Amazon QuickSight <br>&emsp; + Amazon Bedrock                                                                               | 27/05/2025   | 27/05/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 6:
* Khả năng tối ưu giao diện và bảo mật nền tảng Web:
    * Triển khai ứng dụng nhanh: Nắm vững cách sử dụng AWS Amplify để tự động hóa quy trình CI/CD và kết nối backend nhanh chóng cho các dự án Web/Mobile.
    * Tăng tốc và bảo vệ nội dung: Hiểu cơ chế thiết lập phân phối nội dung toàn cầu qua CloudFront (CDN) và cách cấu hình tường lửa AWS WAF để ngăn chặn các cuộc tấn công DDoS hoặc bot độc hại đâm thẳng vào cơ sở dữ liệu.

* Làm chủ luồng định tuyến API và Điện toán phi máy chủ:
    * Quản lý cửa ngõ API: Nắm bắt quy trình thiết lập API Gateway làm điểm tiếp nhận, kiểm tra tính hợp lệ và định tuyến các request từ giao diện người dùng.
    * Xử lý Event-driven: Hiểu cách ứng dụng AWS Lambda để chạy logic code theo từng sự kiện (ví dụ: tự động xử lý yêu cầu điểm danh QR tức thì) mà không cần duy trì hoặc trả phí cho máy chủ chạy 24/7.

* Tư duy vận hành hệ thống Microservices bằng Container:
    * Quản lý nội bộ AWS: Hiểu rõ cơ chế điều phối "thùng hàng" ứng dụng của AWS ECS, mang lại sự tiện lợi cao khi liên kết với các dịch vụ mạng nội bộ khác của hệ thống.
    * Tiêu chuẩn mở rộng toàn cầu: Nắm bắt kiến trúc của AWS EKS dựa trên tiêu chuẩn Kubernetes, phục vụ cho việc mở rộng hạ tầng phần mềm linh hoạt, cấp phép mạng lưới sâu hơn và tránh tình trạng khóa chặt vào một nhà cung cấp đám mây.

* Giải quyết bài toán quá tải bằng Xử lý luồng thời gian thực:
    * Hứng dữ liệu Real-time: Hiểu cơ chế tiếp nhận luồng dữ liệu khổng lồ, liên tục từ thiết bị người dùng cuối thông qua Amazon Kinesis.
    * VXử lý bất đồng bộ: Làm chủ khái niệm hàng đợi thông điệp (Pub/Sub) của Amazon MSK. Hiểu cách dùng Kafka làm kho đệm (buffer) để hệ thống xử lý ngầm, đảm bảo ứng dụng không bị sập hay treo máy khi có hàng trăm sinh viên cùng thao tác gửi yêu cầu một lúc.s

* Kiến trúc luồng tích hợp và xử lý dữ liệu quy mô lớn: 
  * Tự động hóa ETL: Nắm vững quy trình tự động trích xuất, làm sạch và chuẩn hóa dữ liệu thô từ nhiều nguồn khác nhau bằng AWS Glue.
  * Xử lý khối dữ liệu khổng lồ: Hiểu phương pháp vận hành Amazon EMR để huy động các cụm máy chủ công nghiệp (sử dụng Hadoop, Spark) nhằm tính toán các tệp dữ liệu lịch sử siêu lớn.

* Khai thác dữ liệu kinh doanh và Tích hợp Trí tuệ nhân tạo:
  * Truy vấn siêu tốc: Nắm bắt cách tổ chức và lưu trữ dữ liệu sạch trong Data Warehouse (Amazon Redshift) để phục vụ cho các câu lệnh truy vấn phân tích phức tạp với tốc độ cực cao.
  * Báo cáo trực quan: Biết cách trích xuất dữ liệu từ Redshift vào Amazon QuickSight để thiết kế các bảng điều khiển (Dashboard) báo cáo quản trị tương tác.
  * Tích hợp AI an toàn: Hiểu quy trình dùng Amazon Bedrock làm lớp trung gian bảo mật, cho phép gọi các mô hình AI ngôn ngữ lớn (LLM) để xây dựng tính năng AI vào hệ thống mà vẫn giữ kín tuyệt đối dữ liệu nội bộ.