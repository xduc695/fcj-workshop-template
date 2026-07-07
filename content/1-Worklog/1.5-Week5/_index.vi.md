---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu tuần 5:

* Thực hành quản trị và bảo mật tài nguyên AWS với IAM, trọng tâm vào việc áp dụng nguyên tắc đặc quyền tối thiểu, cấu hình IAM Role và thiết lập các Condition giới hạn truy cập để tăng cường an toàn hệ thống.
* Thực hành triển khai tính năng IAM Permission Boundary để thiết lập giới hạn đặc quyền tối đa cho người dùng, giúp quản lý phân quyền hiệu quả và ngăn chặn rủi ro privilege escalation trong hệ thống AWS.
* Thực hành kiểm soát truy cập và phân quyền tài nguyên EC2 dựa trên Resource Tag bằng AWS IAM, áp dụng nguyên tắc đặc quyền tối thiểu thông qua việc thiết lập các Policy với điều kiện ràng buộc cụ thể nhằm phục vụ công tác quản trị hệ thống phi tập trung.
* Thực hành triển khai AWS Security Hub và AWS Config để thiết lập trung tâm giám sát an ninh toàn diện, giúp đánh giá trạng thái tuân thủ của hệ thống dựa trên các tiêu chuẩn bảo mật cốt lõi (CIS, PCI DSS, AWS Foundational) và thực hiện quản lý, tùy chỉnh các cảnh báo rủi ro.
* Thực hành triển khai giải pháp mã hóa dữ liệu ở trạng thái lưu trữ trên Amazon S3 bằng AWS KMS, đồng thời thiết lập cơ chế giám sát an ninh toàn diện bằng cách tích hợp AWS CloudTrail để ghi nhật ký sự kiện và Amazon Athena để truy vấn dữ liệu kiểm toán.
* Tìm hiểu về dịch vụ cơ sở dữ liệu trên AWS.
* Thực hành ôn lại cú pháp SQL cơ bản trên W3Schools để phục vụ cho việc quản trị cơ sở dữ liệu.
* Thực hành triển khai và quản trị cơ sở dữ liệu quan hệ trên đám mây với Amazon RDS, kết nối từ EC2 và thực hiện các thao tác vận hành cốt lõi như Backup và Restore dữ liệu.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                                                                                                                              | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Thực hành quản trị và bảo mật tài nguyên AWS với IAM, trọng tâm vào việc áp dụng nguyên tắc đặc quyền tối thiểu, cấu hình IAM Role và thiết lập các Condition giới hạn truy cập để tăng cường an toàn hệ thống <br> - **Thực hành:** <br>&emsp; + Tạo IAM Group có quyền truy cập admin tới 2 dịch vụ EC2 và RDS <br>&emsp; + Tạo và kiểm tra quyền của các IAM User <br>&emsp; + Tạo Admin IAM Role và cấu hình Switch role <br>&emsp; + Cấu hình và thực hiện Role Condition theo IP và time               | 15/05/2026   | 15/05/2026      | <https://000044.awsstudygroup.com/> |                                            
| 2   | - Thực hành triển khai tính năng IAM Permission Boundary để thiết lập giới hạn đặc quyền tối đa cho người dùng, giúp quản lý phân quyền hiệu quả và ngăn chặn rủi ro privilege escalation trong hệ thống AWS <br> - **Thực hành:** <br>&emsp; + Tạo IAM policy để giới hạn quyền tối đa của User <br>&emsp; + Tạo và giới hạn quyền lên IAM User <br>&emsp;+ Kiểm tra quyền của IAM User <br> - Thực hành kiểm soát truy cập và phân quyền tài nguyên EC2 dựa trên Resource Tag bằng AWS IAM, áp dụng nguyên tắc đặc quyền tối thiểu thông qua việc thiết lập các Policy với điều kiện ràng buộc cụ thể nhằm phục vụ công tác quản trị hệ thống phi tập trung <br> - **Thực hành:** <br>&emsp; + Tạo các IAM Policy để kiểm soát EC2 bằng Resource Tag <br>&emsp; + Tạo IAM Role và gắn các policy đã tạo <br>&emsp; + Tiến hành switch role và kiểm tra quyền với các chính đã tạo                                                                                                                                                                                                                        | 16/05/2025   | 16/05/2025      | <https://000030.awsstudygroup.com/><br><https://000028.awsstudygroup.com/> |
| 3   | - Thực hành triển khai AWS Security Hub và AWS Config để thiết lập trung tâm giám sát an ninh toàn diện, giúp đánh giá trạng thái tuân thủ của hệ thống dựa trên các tiêu chuẩn bảo mật cốt lõi (CIS, PCI DSS, AWS Foundational) và thực hiện quản lý, tùy chỉnh các cảnh báo rủi ro <br> - **Thực hành:** <br>&emsp; + Kích hoạt và cấu hình dịch vụ AWS Security Hub cùng AWS Config <br>&emsp; + Kiểm tra, đánh giá và quản lý rủi ro theo các tiêu chuẩn bảo mật (CIS, PCI DSS, AWS Foundational) <br> - Thực hành triển khai giải pháp mã hóa dữ liệu ở trạng thái lưu trữ trên Amazon S3 bằng AWS KMS, đồng thời thiết lập cơ chế giám sát an ninh toàn diện bằng cách tích hợp AWS CloudTrail để ghi nhật ký sự kiện và Amazon Athena để truy vấn dữ liệu kiểm toán<br> - **Thực hành:** <br>&emsp; + Tạo Key Management Service <br>&emsp; + Tạo Bucket và uploads dữ liệu lên Amazon S3 <br>&emsp; + Cấu hình AWS CloudTrail để ghi nhật ký sự kiện <br>&emsp; + Sử dụng Amazon Athena để truy vấn nhật ký <br>&emsp; + Kiểm thử và chia sẻ dữ liệu mã hóa trên S3                                                                                                                                                      | 17/05/2025   | 17/05/2025      | <https://000018.awsstudygroup.com/><br><https://000033.awsstudygroup.com/> |
| 4   | -  Tìm hiểu về dịch vụ cơ sở dữ liệu trên AWS: <br>&emsp; + Database Concepts <br>&emsp; + Amazon RDS & Aurora <br>&emsp; + Amazon Redshift <br>&emsp; + Amazon ElastiCache                                                                                                                                                                                                                       | 18/05/2025   | 18/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Thực hành ôn lại cú pháp SQL cơ bản trên W3Schools để phục vụ cho việc quản trị cơ sở dữ liệu:<br> - **Thực hành:** <br>&emsp; + Ôn tập nhóm lệnh truy vấn dữ liệu <br>&emsp; + Ôn tập nhóm lệnh thao tác và định nghĩa dữ liệu <br>&emsp; + Thực hành viết và chạy thử truy vấn trực tiếp trên W3Schools                                                                                                                                                                                                                                                                                                                 | 19/05/2025   | 19/05/2025      | <https://www.w3schools.com/sql/default.asp> |
| 6   | - Thực hành triển khai và quản trị cơ sở dữ liệu quan hệ trên đám mây với Amazon RDS, kết nối từ EC2 và thực hiện các thao tác vận hành cốt lõi như Backup và Restore dữ liệu <br> - **Thực hành:** <br>&emsp; + Tạo hạ tầng mạng và Security Group cho EC2, RDS, DB <br>&emsp; + Khởi tạo EC2 Instance và RDS database instance <br>&emsp; + TTriển khai ứng dụng và kiểm tra kết nối đến cơ sở dữ liệu <br>&emsp; + Thực hiện quy trình Backup và Restore trên Amazon RDS                                                                                                                                                                                                                                                                                                          | 20/05/2025   | 20/05/2025      | <https://000005.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* Thành thạo cấu hình và kiểm soát truy cập nâng cao với IAM Role:
  * Triển khai thành công cơ chế Switch Role, đảm bảo cấp quyền quản trị tạm thời theo nguyên tắc đặc quyền tối thiểu.
  * Cấu hình và kiểm chứng hiệu quả các ràng buộc (Condition); hệ thống tự động chặn truy cập (Access Denied) khi sai địa chỉ IP hoặc ngoài khung giờ cho phép.

![IAM Condition](/images/68.png)

* Triển khai thành công IAM Permission Boundary để ngăn chặn rủi ro leo thang đặc quyền (Privilege Escalation):
  * Thiết lập và áp dụng chính sách giới hạn quyền tối đa (Maximum Permissions), cấu hình này thành công ghi đè và kiểm soát chặt chẽ các policy cấp quyền cao (Full Access) của IAM User.
  * Kiểm chứng thực tế hiệu lực phân quyền: Hệ thống cấp quyền truy cập EC2 hợp lệ tại khu vực được chỉ định (ví dụ: Singapore) và tự động vô hiệu hóa mọi thao tác quản trị (báo lỗi không có quyền) khi chuyển sang khu vực ngoài phạm vi (ví dụ: Tokyo)

  ![IAM Permission Boundary](/images/69.png)

* Thực hiện thành công phân quyền quản trị EC2 phi tập trung dựa trên Resource Tag:
  * Xây dựng chuỗi IAM Policy với điều kiện khắt khe: buộc người dùng chỉ được phép khởi tạo và quản lý tài nguyên EC2 khi gắn chính xác bộ thẻ định danh quy định (ví dụ: Team=Alpha).
  * Kiểm chứng tính chặt chẽ của hệ thống: Tự động chặn đứng (Launch Failed) các yêu cầu tạo mới EC2 sai thẻ, đồng thời từ chối quyền truy cập khi người dùng cố tình chỉnh sửa hoặc xóa bỏ Resource Tag của tài nguyên đang chạy.

  ![IAM Resource Tags](/images/70.png)

* Thiết lập thành công trung tâm giám sát an ninh và đánh giá tuân thủ tự động:
  * Tích hợp hoàn thiện AWS Security Hub với dịch vụ nền AWS Config để tự động quét, phát hiện lỗ hổng và chấm điểm an toàn (Security Score) theo thời gian thực.
  * Đánh giá toàn diện trạng thái bảo mật của hệ thống dựa trên việc đối chiếu tự động với 3 bộ tiêu chuẩn quốc tế cốt lõi (AWS Foundational, CIS Benchmark và PCI DSS).

* Nắm vững kỹ năng quản lý và tối ưu hóa cấu hình an ninh đám mây: 
  * Khai thác hiệu quả giao diện Dashboard để phân tích, phân loại mức độ nghiêm trọng của các cảnh báo rủi ro hệ thống.
  * Làm chủ kỹ năng tùy chỉnh bộ quy tắc an ninh thông qua tác vụ vô hiệu hóa (Disable control) các tiêu chí không phù hợp với thực tế vận hành (Not aligned to risk threshold).

  ![Security Hub](/images/71.png)

* Triển khai thành công giải pháp mã hóa dữ liệu lưu trữ (Encryption at Rest) và kiểm soát quyền truy cập:
  * Thiết lập cơ chế mã hóa tự động cho Amazon S3 (SSE-KMS) sử dụng khóa bảo mật tự quản lý (Customer Managed Key) từ AWS KMS.
  * Kiểm chứng hiệu quả bảo mật: Hệ thống chặn đứng (Access Denied) mọi nỗ lực truy cập từ người dùng nội bộ không có quyền giải mã KMS và từ chối các truy cập Public trực tiếp.
  * Thực hiện chia sẻ dữ liệu mã hóa an toàn cho bên thứ ba thông qua cơ chế Presigned URL với thời hạn truy cập bị giới hạn nghiêm ngặt (2 phút).
  
  ![Access Denied](/images/73.png)

* Thiết lập luồng giám sát an ninh và kiểm toán dữ liệu toàn diện:
  * Cấu hình AWS CloudTrail tự động ghi nhận nhật ký thao tác dữ liệu (Data Events) trên S3 theo thời gian thực.
  * Tích hợp thành công Amazon Athena, thực thi trơn tru các câu lệnh SQL để truy xuất, phân tích và tra cứu chi tiết lịch sử sự kiện (eventname) từ kho dữ liệu log.

![Amazon Athena](/images/72.png)

* Hệ thống hóa toàn diện kiến thức nền tảng về các dịch vụ Database cốt lõi trên đám mây AWS:
    * Database Concepts: Nắm vững cách phân loại Database và hình thành tư duy lựa chọn đúng dịch vụ (Relational, Non-relational, In-memory, Data Warehouse) cho từng bài toán cụ thể của hệ thống.
    * Amazon RDS & Aurora: Hiểu rõ cơ chế vận hành của RDBMS dưới dạng Managed Service trên AWS, đặc biệt nắm bắt kiến trúc Cloud-native giúp tối ưu hiệu suất và khả năng mở rộng vượt trội của Amazon Aurora.
    * Amazon Redshift: Phân biệt rõ bản chất giữa hệ thống OLTP và OLAP, hiểu được vai trò của Data Warehouse trong việc xử lý và phân tích khối lượng dữ liệu khổng lồ ở quy mô Petabyte.
    * Amazon ElastiCache: Nắm bắt cơ chế hoạt động của In-memory caching, hiểu cách ứng dụng Redis hoặc Memcached để giảm tải cho Database chính và tối ưu hóa latency cho ứng dụng.

* Củng cố vững chắc kiến thức nền tảng về truy vấn và thao tác dữ liệu (SQL):
    * Nắm vững cú pháp và tư duy thiết lập các nhóm lệnh DML, DDL cùng các truy vấn phức tạp (JOIN, GROUP BY, HAVING).
    * Thực thi thành công các câu lệnh SQL trực tiếp trên môi trường giả lập của W3Schools, đảm bảo trích xuất và xử lý dữ liệu chính xác theo điều kiện đầu vào.
    * Hoàn thiện bước đệm kỹ thuật quan trọng, sẵn sàng cho công tác vận hành và quản trị RDBMS trực tiếp trên hạ tầng Amazon RDS.

![SQL](/images/74.png)

* Triển khai cơ sở dữ liệu Amazon RDS và kết nối ứng dụng:
  * Khởi tạo thành công RDS database instance và thiết lập liên kết thông suốt từ ứng dụng Node.js thông qua file môi trường cấu hình Endpoint và Credentials.
  * Thực thi các lệnh SQL tạo cấu trúc Database, Table và import thành công bộ dữ liệu mẫu, đảm bảo ứng dụng hiển thị và truy xuất dữ liệu mượt mà trên trình duyệt.

![RDS](/images/75.png)

* Vận hành thành công quy trình Backup và Restore dữ liệu:
  * Chủ động khởi tạo DB Snapshot thủ công để lưu trữ trạng thái an toàn của hệ thống cơ sở dữ liệu.
  * Thực hiện Restore thành công một DB instance hoàn toàn mới từ bản Snapshot hiện có, nắm vững quy trình cập nhật Endpoint mới vào Connection String để đảm bảo ứng dụng không bị gián đoạn.

![Restore](/images/76.png)