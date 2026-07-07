---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu tuần 9:

* Ôn tập và củng cố lại toàn bộ kiến thức cốt lõi đã học trên AWS Cloud.
* Nghiên cứu AWS AppSync và thực hành xây dựng API GraphQL để thao tác dữ liệu thời gian thực với DynamoDB.
* Nghiên cứu và thực hành triển khai mã nguồn Front-end lên dịch vụ AWS Amplify Hosting để nhanh chóng phát hành website chạy trên môi trường điện toán đám mây.
* Thực hành đóng gói ứng dụng bằng Docker và triển khai lên AWS EC2 kết nối Amazon ECR và cơ sở dữ liệu RDS.
* Nghiên cứu dịch vụ Amazon ECS và thực hành cấu hình Cluster, Task Definition, Service để triển khai ứng dụng container hóa kết hợp Application Load Balancer.
* Tìm hiểu vế Outbox Pattern để bảo đảm nhất quán dữ liệu liên dịch vụ, kết hợp Resilience4j (Retry, Timeout, Circuit Breaker) nhằm nâng cao năng lực chịu lỗi cho hệ thống Microservices.
* Nghiên cứu các tiêu chuẩn thiết kế hạ tầng AWS và tìm hiểu cách sử dụng công cụ Draw.io để chuẩn bị cho việc trực quan hóa sơ đồ kiến trúc hệ thống.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Ôn tập và củng cố lại toàn bộ kiến thức cốt lõi đã học trên AWS Cloud: <br>&emsp; + Ôn tập lại các dịch vụ mạng trên aws (VPC, VPC Peering, Transit Gateway, ELB). <br>&emsp; + Ôn tập lại các dịch vụ Compute VM trên AWS (Cấu hình và quản lý thực thể EC2). <br>&emsp; + Ôn tập lại các dịch vụ cơ sở dữ liệu trên AWS (Hệ quản trị RDS và NoSQL DynamoDB). <br>&emsp; + Ôn tập lại các dịch vụ lưu trữ trên AWS (Lưu trữ đối tượng với S3 và lưu trữ khối với EBS). <br>&emsp; + Ôn tập lại các dịch vụ bảo mật trên AWS (Quản lý định danh IAM và các lớp tường lửa hệ thống).                                                                                            | 12/06/2026   | 12/06/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 2   | - Nghiên cứu AWS AppSync và thực hành xây dựng API GraphQL để thao tác dữ liệu thời gian thực với DynamoDB <br> - **Thực hành:** <br>&emsp; + Tạo các DynamoDB Resolver <br>&emsp; + Tạo bảng trong DynamoDB và GraphQL API <br>&emsp; + Thực hiện truy vấn hoặc thay đổi dữ liệu bằng cách xác định các Resolver <br>&emsp; + Tạo các đối tượng phức tạp hơn với AWS AppSyncDynamoDB <br> - Nghiên cứu AWS Amplify Hosting và thực hành triển khai ứng dụng web front-end lên môi trường đám mây <br> - **Thực hành:** <br>&emsp; + Đóng gói mã nguồn Front-end bằng lệnh yarn build từ dự án workshop <br>&emsp; + Nén toàn bộ thư mục sản phẩm sau khi build thành định dạng file .zip chuẩn <br>&emsp; + Khởi tạo ứng dụng trên AWS Amplify Console bằng phương thức thủ công (Deploy without Git) <br>&emsp; + Tiến hành kéo thả file .zip để phát hành website chạy trực tiếp trên Internet <br>&emsp; + Truy cập và kiểm tra hoạt động của giao diện web qua đường dẫn mặc định do AWS cấp                                           | 13/06/2026   | 13/06/2026      | <https://000086.awsstudygroup.com/> |
| 3   | - Thực hành đóng gói ứng dụng bằng Docker và triển khai lên AWS EC2 kết nối Amazon ECR và cơ sở dữ liệu RDS <br> - **Thực hành:** <br>&emsp; + Cài đặt Dependencies , triển khai và kiểm tra ứng dung trên môi trương local <br>&emsp; + Tạo DB Subnet Group và khởi chạy RDS Instance <br>&emsp; + Cấu hình cho EC2 Instance <br>&emsp; + Cài đặt các thư viện yêu cầu và thêm cơ sở dữ liệu <br>&emsp; + Triển khai và kiểm tra Application trên Docker Image <br>&emsp; + Triển khai và kiểm tra Application trên Docker Compose <br>&emsp; + Tạo và push Image lên ECR Repository <br>&emsp; + Push Image lên Docker Hub | 14/06/2026   | 14/06/2026      | <https://000015.awsstudygroup.com/> |
| 4   | - Nghiên cứu dịch vụ Amazon ECS và thực hành cấu hình Cluster, Task Definition, Service để triển khai ứng dụng container hóa kết hợp Application Load Balancer <br> - **Thực hành:** <br>&emsp; + Tải Docker frontend image lên ECR <br>&emsp; + Đăng ký namespace trong Cloud Map <br>&emsp; + Tạo ECS Cluster <br>&emsp; + Tạo ECS backend và frontend Task Definitions <br>&emsp; + Triển khai và kiểm tra Application trên Docker Image <br>&emsp; + Tạo Target Group <br>&emsp; + Cấu hình Application Load Balancer <br>&emsp; + Triển khai rolling và Service Scaling với Backend  <br>&emsp; + Kiểm tra kết quả | 15/06/2026   | 15/06/2026      | <https://000016.awsstudygroup.com/> |
| 5   | - Nghiên cứu lý thuyết Outbox Pattern và giải pháp chịu lỗi với Resilience4j: <br>&emsp; + Tìm hiểu nguyên lý hoạt động của kiến trúc Transactional Outbox Pattern nhằm bảo đảm tính nhất quán dữ liệu (Data Consistency) giữa các Microservices. <br>&emsp; + Nghiên cứu cơ chế vận hành và tham số cấu hình của cơ chế Retry (tự động thử lại) và Timeout (ngắt kết nối quá hạn). <br>&emsp; + Tìm hiểu nguyên lý hoạt động và các trạng thái (Closed, Open, Half-Open) của Circuit Breaker trong Resilience4j. | 16/06/2026   | 16/06/2026      | 
| 6   | - Nghiên cứu tiêu chuẩn thiết kế hạ tầng AWS và tìm hiểu công cụ thiết kế sơ đồ Draw.io: <br>&emsp; + Tìm hiểu các nguyên tắc cốt lõi trong khung chuẩn thiết kế hạ tầng tối ưu của AWS (AWS Well-Architected Framework). <br>&emsp; + Nghiên cứu bộ ký hiệu, biểu tượng chuẩn của AWS (AWS Architecture Icons) đại diện cho các dịch vụ mạng, máy chủ và cơ sở dữ liệu. <br>&emsp; + Tìm hiểu cách sử dụng công cụ Draw.io để làm quen với các thao tác kéo thả, liên kết tài nguyên và quản lý layer khi vẽ sơ đồ kiến trúc. | 17/06/2026   | 17/06/2026      | <https://youtu.be/l8isyDe-GwY?si=dS13yhJKd8bE55na> |

### Kết quả đạt được tuần 9:
* Ôn tập hệ thống dịch vụ Mạng (Networking) và Bảo mật (Security) trên AWS:
  * Hệ thống hóa thành công lý thuyết và cơ chế hoạt động của Amazon VPC, phân định rõ vai trò của Subnet, Route Table, Internet Gateway, và dịch vụ định tuyến Route 53.
  * Củng cố vững chắc nguyên lý kết nối mở rộng hệ thống thông qua VPC Peering và Transit Gateway, cùng các giải pháp cân bằng tải Elastic Load Balancing (ELB).
  * Nắm vững phương thức phân quyền nghiêm ngặt bằng IAM (Users, Groups, Roles, Policies) và cơ chế thiết lập tường lửa đa lớp bảo vệ tài nguyên thông qua Security Groups và Network ACLs.

* Ôn tập hệ thống dịch vụ Máy chủ (Compute), Lưu trữ (Storage) và Cơ sở dữ liệu (Database):
  * Cấu trúc lại toàn bộ quy trình khởi tạo, quản lý vòng đời (Start, Stop, Terminate) và cấu hình tối ưu hiệu năng/chi phí cho các thực thể máy chủ ảo Amazon EC2.
  * Phân biệt rõ ràng hai giải pháp lưu trữ cốt lõi: lưu trữ đối tượng linh hoạt với Amazon S3 (quản lý Bucket Policy, Lifecycle Rule) và lưu trữ khối hiệu năng cao Amazon EBS gắn kèm máy chủ.
  * Hệ thống hóa đặc điểm vận hành, kịch bản áp dụng thực tế và cách điều phối dữ liệu giữa hệ quản trị cơ sở dữ liệu quan hệ Amazon RDS và cơ sở dữ liệu NoSQL Amazon DynamoDB.

  * Thiết lập kiến trúc GraphQL API và phân phối dữ liệu qua AWS AppSync:
  * Khởi tạo thành công GraphQL API (`AWSAppSyncTutorial`) bằng phương thức Wizard và xây dựng hoàn chỉnh tệp GraphQL Schema để quản trị cấu trúc dữ liệu của các `Post` và `Comment`.
  * Liên kết thành công AppSync với nguồn dữ liệu NoSQL thông qua bảng DynamoDB (`AppSyncTutorial-Post`), đồng thời tự động hóa quy trình ủy quyền phân quyền an toàn bằng IAM Role.

* Triển khai hệ thống DynamoDB Resolvers điều phối dữ liệu:
  * Lập trình và cấu hình thành công các bộ Request/Response Mapping Templates sử dụng ngôn ngữ VTL để ánh xạ trực tiếp các phương thức GraphQL Mutations (`addPost`, `updatePost`, `deletePost`) và Queries (`getPost`, `allPost`) xuống cơ sở dữ liệu.
  * Tích hợp thành công biểu thức điều kiện `expectedVersion` giúp kiểm soát phiên bản dữ liệu một cách tối ưu, ngăn chặn triệt để xung đột đồng thời khi có nhiều người dùng cùng chỉnh sửa bản ghi.
  * Thiết kế thành công các cấu trúc dữ liệu phức tạp bao gồm các tập hợp danh sách (`SS` - String Set cho thuộc tính tags) và danh sách lồng bản đồ (`L` & `M` - List & Map cho hệ thống comments) bằng hàm `list_append`.

* Kết quả nghiệm thu thực nghiệm trên AppSync Console:
  * Thực thi thành công các câu lệnh GraphQL Queries và Mutations trực tiếp trên tab Queries, dữ liệu được ghi nhận, cập nhật và đồng bộ hóa thời gian thực (Real-time) sang bảng DynamoDB.
  * Nghiệm thu cơ chế phân trang hoạt động chính xác thông qua giá trị token `nextToken` thu được sau mỗi chu kỳ quét dữ liệu (`Scan`).

  ![GraphQL API Execution Result](/images/92.png)

  ![DynamoDB Item Verification](/images/93.png)

* Triển khai thành công ứng dụng Front-end lên môi trường đám mây bằng AWS Amplify Hosting:
  * Đóng gói thành công mã nguồn ứng dụng web bán sách từ dự án workshop thành định dạng file nén .zip chuẩn cấu hình.
  * Khởi tạo và phát hành ứng dụng tĩnh thông qua phương thức triển khai thủ công (Deploy without Git) trên AWS Amplify Console một cách nhanh chóng.

![AWS Amplify Deployment Success](/images/94.png)

* Kích hoạt và kiểm tra tính sẵn sàng của website trên môi trường Internet:
  * AWS Amplify cấp phát tự động đường dẫn mặc định (domain dạng amplifyapp.com) hoạt động ổn định.
  * Truy cập thực tế vào giao diện website, kiểm tra các tính năng hiển thị của cửa hàng sách đều hoạt động mượt mà trên môi trường Cloud.

![Website UI via Amplify Domain](/images/95.png)

* Triển khai ứng dụng Container hóa bằng Docker và Docker Compose:
  * Đóng gói thành công Frontend và Backend thành các Docker Images (`frontend-image`, `backend-image`) độc lập trực tiếp trên máy chủ EC2.
  * Thiết lập mạng nội bộ `my-network` kết nối an toàn với cơ sở dữ liệu Amazon RDS và ánh xạ cổng dịch vụ qua Nginx Reverse Proxy.
  * Tối ưu hóa chu trình quản lý bằng Docker Compose, tự động hóa toàn bộ quy trình khởi chạy và điều phối các Container thông qua tệp `docker-compose.app.yml`.

* Đẩy tải và lưu trữ hình ảnh lên AWS ECR và Docker Hub:
  * Gắn Role IAM và xác thực tài khoản thành công qua AWS CLI để tương tác an toàn giữa EC2 và Amazon Elastic Container Registry (ECR).
  * Khởi tạo thành công các Repository quản lý mã nguồn (`fcjresbar-fe`, `fcjresbar-be`) trên cả hai nền tảng AWS ECR và Docker Hub công khai.
  * Thực hiện gắn thẻ (`docker tag`) và đẩy (push) thành công các Docker Images lên hệ thống lưu trữ, sẵn sàng phục vụ cho quy trình CI/CD.

* Kết quả thực nghiệm kiểm thử hệ thống:
  * Ứng dụng vận hành ổn định qua IP công khai của EC2 tại cổng `3000`, giao diện phản hồi trực quan.
  * Luồng xác thực đăng nhập (Admin/User) và kết nối truy vấn dữ liệu thời gian thực về Amazon RDS MySQL hoạt động trơn tru.
  ![Docker Application Verification](/images/96.png)
  ![ECR Container Images Storage](/images/97.png)

* Đóng gói và đẩy Docker Images lên Amazon ECR:
  * Khởi tạo thành công hai kho lưu trữ riêng biệt cho Frontend và Backend trên Amazon ECR.
  * Biên dịch mã nguồn thành Docker Images và đẩy lên ECR thành công với nhãn cấu hình latest.

* Khởi tạo hạ tầng Amazon ECS Cluster và Task Definitions:
  * Thiết lập cụm tài nguyên FCJ-Lab-cluster vận hành trên nền tảng Serverless AWS Fargate.
  * Đăng ký hoàn chỉnh thông số cấu hình cấu hình trong hai bộ Task Definition fcjresbar-task-fe và fcjresbar-task-be.

![ECS Cluster Task Definitions](/images/98.png)

* Triển khai ứng dụng và nghiệm thu trạng thái hệ thống:
  * Kích hoạt thành công hai dịch vụ Frontend và Backend trên cụm ECS ở trạng thái ACTIVE.
  * Xác minh tiến trình vận hành, ghi nhận toàn bộ các tác vụ đều khởi động và duy trì ở trạng thái RUNNING.

![ECS Cluster Services](/images/99.png)

* Nghiên cứu giải pháp nhất quán dữ liệu với Transactional Outbox Pattern:
  * Làm chủ nguyên lý hoạt động của Outbox Pattern nhằm giải quyết triệt để bài toán mất mát dữ liệu sự kiện (Event) khi xảy ra lỗi mạng giữa các Microservices.
  * Hiểu rõ cơ chế sử dụng một bảng trung gian (`Outbox Table`) nằm cùng cơ sở dữ liệu với nghiệp vụ chính để đảm bảo tính toàn vẹn giao dịch (ACID Transaction).
  * Định hình được quy trình vận hành của một dịch vụ quét ngầm (Message Relay/Debezium) để đọc dữ liệu từ bảng Outbox và xuất bản (Publish) chính xác sang Message Broker.

* Hệ thống hóa lý thuyết chịu lỗi hệ thống với Resilience4j:
  * Nắm vững cơ chế vận hành và các tham số cấu hình cốt lõi của tính năng Retry (số lần thử lại tối đa, khoảng thời gian chờ `waitDuration`) đối với các sự cố bất định, ngắn hạn.
  * Hiểu rõ tầm quan trọng của cơ chế Timeout trong việc thiết lập giới hạn thời gian phản hồi tối đa, ngăn chặn tình trạng nghẽn cổ chai và treo luồng hệ thống (Thread Starvation).
  * Làm chủ nguyên lý chuyển đổi trạng thái của Circuit Breaker bao gồm 3 trạng thái đóng mạch (`Closed`), mở mạch (`Open`) để ngắt kết nối tạm thời bảo vệ dịch vụ phía sau, và thử nghiệm phục hồi (`Half-Open`).

* Nghiên cứu tiêu chuẩn kiến trúc AWS Well-Architected Framework:
  * Tiếp thu sâu sắc 6 trụ cột cốt lõi của khung chuẩn thiết kế hạ tầng AWS nhằm đảm bảo hệ thống vận hành an toàn, hiệu quả, có khả năng chịu lỗi và tối ưu hóa chi phí.
  * Hiểu rõ các nguyên tắc thiết kế hệ thống có tính sẵn sàng cao (High Availability), phân tán đa vùng tin cậy (Multi-AZ) và khả năng mở rộng linh hoạt (Scalability).

* Làm chủ bộ ký hiệu chuẩn hóa AWS Architecture Icons:
  * Nhận diện và phân loại chính xác bộ biểu tượng dịch vụ chuẩn hóa mới nhất của AWS cho các nhóm tài nguyên cốt lõi: Compute (EC2), Database (RDS, DynamoDB), Storage (S3, EBS) và Networking (VPC, Transit Gateway, ALB).
  * Hiểu rõ quy chuẩn sử dụng màu sắc, các đường liên kết mũi tên điều hướng và cách gom nhóm tài nguyên (Grouping) theo phân vùng bảo mật Subnet/VPC trên sơ đồ.

* Thành thạo công cụ trực quan hóa sơ đồ kiến trúc Draw.io:
  * Làm quen và sử dụng thành thạo giao diện làm việc của Draw.io, biết cách tích hợp bộ thư viện biểu tượng AWS chính thức vào vùng quản lý công cụ.
  * Nắm vững các thao tác kỹ thuật kéo thả, kết nối liên kết động giữa các thành phần tài nguyên và kỹ thuật quản lý phân tầng (Layers) để chuẩn bị cho việc thiết kế các sơ đồ kiến trúc hệ thống phức tạp phía sau.

