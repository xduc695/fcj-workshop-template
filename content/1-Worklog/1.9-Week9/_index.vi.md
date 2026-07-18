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
* Nghiên cứu và thực hành triển khai mã nguồn Front-end lên dịch vụ AWS Amplify Hosting để nhanh chóng phát hành website.
* Thực hành đóng gói ứng dụng bằng Docker và triển khai lên AWS EC2 kết nối Amazon ECR và cơ sở dữ liệu RDS.
* Nghiên cứu dịch vụ Amazon ECS và thực hành cấu hình Cluster, Task Definition, Service triển khai ứng dụng container hóa kết hợp ALB.
* Tìm hiểu về Outbox Pattern để bảo đảm nhất quán dữ liệu liên dịch vụ, kết hợp Resilience4j nhằm nâng cao năng lực chịu lỗi.
* Nghiên cứu các tiêu chuẩn thiết kế hạ tầng AWS và tìm hiểu cách sử dụng công cụ Draw.io.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Ôn tập toàn bộ kiến thức cốt lõi đã học trên AWS Cloud: <br>&emsp; + Ôn tập mạng (VPC, VPC Peering, Transit Gateway, ELB). <br>&emsp; + Ôn tập Compute VM (EC2). <br>&emsp; + Ôn tập cơ sở dữ liệu (RDS và DynamoDB). <br>&emsp; + Ôn tập lưu trữ (S3 và EBS). <br>&emsp; + Ôn tập bảo mật (IAM và Security Groups).<br> - Nghiên cứu AWS AppSync, thực hành xây dựng API GraphQL thao tác dữ liệu thời gian thực với DynamoDB: <br> - **Thực hành:** <br>&emsp; + Tạo các DynamoDB Resolver <br>&emsp; + Tạo bảng DynamoDB và GraphQL API <br>&emsp; + Thực hiện truy vấn hoặc thay đổi dữ liệu bằng cách xác định các Resolver <br>&emsp; + Tạo các đối tượng phức tạp hơn với AWS AppSyncDynamoDB | 15/06/2026 | 15/06/2026 | <https://cloudjourney.awsstudygroup.com/><br><https://000086.awsstudygroup.com/> |
| Thứ 3 | - Thực hành triển khai ứng dụng web front-end lên môi trường đám mây với AWS Amplify Hosting: <br> - **Thực hành:** <br>&emsp; + Đóng gói mã nguồn Front-end bằng lệnh yarn build <br>&emsp; + Nén toàn bộ thư mục sản phẩm sau khi build thành định dạng file .zip <br>&emsp; + Khởi tạo ứng dụng trên AWS Amplify Console bằng phương thức thủ công (Deploy without Git) <br>&emsp; + Tiến hành kéo thả file .zip để phát hành website <br>&emsp; + Truy cập và kiểm tra giao diện web<br> - Thực hành đóng gói Docker và triển khai EC2 kết nối ECR và RDS: <br> - **Thực hành:** <br>&emsp; + Cài đặt Dependencies, triển khai và kiểm tra trên local <br>&emsp; + Tạo DB Subnet Group và RDS Instance <br>&emsp; + Cấu hình cho EC2 Instance <br>&emsp; + Triển khai và kiểm tra Application trên Docker Image và Docker Compose <br>&emsp; + Tạo và push Image lên ECR và Docker Hub | 16/06/2026 | 16/06/2026 | <https://000015.awsstudygroup.com/> |
| Thứ 4 | - Nghiên cứu Amazon ECS và thực hành cấu hình Cluster, Task, Service triển khai ứng dụng container hóa kết hợp ALB: <br> - **Thực hành:** <br>&emsp; + Tải Docker frontend image lên ECR <br>&emsp; + Đăng ký namespace trong Cloud Map <br>&emsp; + Tạo ECS Cluster <br>&emsp; + Tạo ECS backend và frontend Task Definitions <br>&emsp; + Tạo Target Group <br>&emsp; + Cấu hình Application Load Balancer <br>&emsp; + Triển khai rolling và Service Scaling với Backend <br>&emsp; + Kiểm tra kết quả | 17/06/2026 | 17/06/2026 | <https://000016.awsstudygroup.com/> |
| Thứ 5 | - Nghiên cứu lý thuyết Outbox Pattern và giải pháp chịu lỗi với Resilience4j: <br>&emsp; + Tìm hiểu nguyên lý hoạt động của kiến trúc Transactional Outbox Pattern nhằm bảo đảm tính nhất quán dữ liệu (Data Consistency). <br>&emsp; + Nghiên cứu cơ chế vận hành và tham số cấu hình của cơ chế Retry (tự động thử lại) và Timeout (ngắt kết nối quá hạn). <br>&emsp; + Tìm hiểu nguyên lý hoạt động và các trạng thái (Closed, Open, Half-Open) của Circuit Breaker trong Resilience4j. | 18/06/2026 | 18/06/2026 | |
| Thứ 6 | - Nghiên cứu tiêu chuẩn thiết kế hạ tầng AWS và tìm hiểu công cụ thiết kế sơ đồ Draw.io: <br>&emsp; + Tìm hiểu các nguyên tắc cốt lõi trong khung chuẩn thiết kế hạ tầng tối ưu của AWS (AWS Well-Architected Framework). <br>&emsp; + Nghiên cứu bộ ký hiệu, biểu tượng chuẩn của AWS (AWS Architecture Icons) đại diện cho các dịch vụ mạng, máy chủ và cơ sở dữ liệu. <br>&emsp; + Tìm hiểu cách sử dụng công cụ Draw.io để làm quen với các thao tác kéo thả, liên kết tài nguyên và quản lý layer khi vẽ sơ đồ kiến trúc. | 19/06/2026 | 19/06/2026 | <https://youtu.be/l8isyDe-GwY?si=dS13yhJKd8bE55na> |

### Kết quả đạt được tuần 9:

**1. Ôn tập & Triển khai AppSync GraphQL (Thứ 2)**
* Hệ thống hóa thành công lý thuyết Amazon VPC, ELB, EC2, S3, EBS, RDS, DynamoDB, IAM và Security Groups.
* Khởi tạo GraphQL API (`AWSAppSyncTutorial`), xây dựng tệp GraphQL Schema quản trị `Post` và `Comment`. Liên kết AppSync với bảng DynamoDB, ủy quyền IAM Role.
* Lập trình Request/Response Mapping Templates (VTL) ánh xạ GraphQL Mutations (`addPost`, `updatePost`, `deletePost`) và Queries. Tích hợp `expectedVersion` chống xung đột.
* Thực thi thành công Queries và Mutations trên Console, dữ liệu đồng bộ thời gian thực.
![GraphQL API Execution Result](/images/92.png)
![DynamoDB Item Verification](/images/93.png)

**2. Amplify Hosting & Docker EC2 (Thứ 3)**
* Đóng gói mã nguồn web thành file `.zip`, khởi tạo ứng dụng trên Amplify Console (Deploy without Git). Amplify tự động cấp phát domain.
![AWS Amplify Deployment Success](/images/94.png)
![Website UI via Amplify Domain](/images/95.png)
* Đóng gói Frontend/Backend thành Docker Images, thiết lập mạng `my-network` kết nối Amazon RDS và ánh xạ cổng qua Nginx. Tối ưu bằng `docker-compose.app.yml`.
* Gắn IAM Role, đẩy Docker Images lên Amazon ECR và Docker Hub công khai. Luồng đăng nhập và truy vấn DB hoạt động trơn tru trên cổng 3000.
![Docker Application Verification](/images/96.png)
![ECR Container Images Storage](/images/97.png)

**3. Triển khai Amazon ECS Cluster & ALB (Thứ 4)**
* Thiết lập cụm `FCJ-Lab-cluster` trên AWS Fargate. Đăng ký thông số `fcjresbar-task-fe` và `fcjresbar-task-be`.
![ECS Cluster Task Definitions](/images/98.png)
* Kích hoạt hai dịch vụ Frontend và Backend trên cụm ECS (trạng thái ACTIVE). Cấu hình Application Load Balancer và Service Scaling thành công.
![ECS Cluster Services](/images/99.png)

**4. Nghiên cứu Outbox Pattern & Resilience4j (Thứ 5)**
* Nắm vững Transactional Outbox Pattern sử dụng bảng trung gian (`Outbox Table`) và Message Relay/Debezium đảm bảo tính toàn vẹn giao dịch (ACID).
* Hiểu rõ cơ chế Retry (`waitDuration`), Timeout chống nghẽn cổ chai (Thread Starvation) và 3 trạng thái của Circuit Breaker (`Closed`, `Open`, `Half-Open`) bảo vệ dịch vụ.

**5. Kiến trúc AWS & Draw.io (Thứ 6)**
* Tiếp thu 6 trụ cột cốt lõi AWS Well-Architected Framework (High Availability, Multi-AZ, Scalability).
* Nhận diện bộ AWS Architecture Icons. Thành thạo thao tác Draw.io, quản lý phân tầng (Layers) chuẩn bị thiết kế sơ đồ kiến trúc phức tạp.
