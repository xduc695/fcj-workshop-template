---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Tìm hiểu về dịch vụ lưu trữ trên AWS.
* Thực hành triển khai website tĩnh trên S3, đồng thời nắm vững các kỹ năng quản trị, bảo mật và dự phòng dữ liệu qua việc phân quyền, quản lý phiên bản, sao chép liên vùng và tìm hiểu tăng tốc truy cập bằng CloudFront với cách khắc phục sự cố S3.
* Thực hành thiết lập kế hoạch sao lưu và khôi phục tự động cho các tài nguyên AWS bằng AWS Backup, kết hợp cấu hình thông báo qua AWS SNS để giám sát và đảm bảo an toàn dữ liệu.
* Thực hành triển khai AWS File Storage Gateway nhằm thiết lập hệ thống chia sẻ tệp (File Share), giúp kết nối và đồng bộ dữ liệu liền mạch giữa môi trường On-premise và lưu trữ đám mây Amazon S3.
* Thực hành triển khai hệ thống lưu trữ tệp dùng chung hiệu năng cao trên môi trường Windows với Amazon FSx, đồng thời làm chủ các kỹ năng quản trị nâng cao như chống trùng lặp dữ liệu, shadow copy, phân bổ hạn mức người dùng và mở rộng tài nguyên linh hoạt.
* Tìm hiểu về dịch vụ bảo mật trên AWS.
* Thực hành các thao tác quản trị truy cập cơ bản trên AWS (IAM) thông qua việc thiết lập User, phân nhóm Group, gán Policy và đồng thời áp dụng cơ chế bảo mật nâng cao bằng cách Switch Role theo nguyên tắc đặc quyền tối thiểu.
* Thực hành phương pháp bảo mật tối ưu để cấp quyền cho ứng dụng truy cập an toàn vào các dịch vụ AWS bằng IAM Role, thay thế hoàn toàn cho việc sử dụng Access Key tiềm ẩn rủi ro lộ lọt dữ liệu.
### Các công việc cần triển khai trong tuần này:
| Ngày  | Công việc                                                                                                                                                                                                                                                                                                                               | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1     | - Tìm hiểu về dịch vụ lưu trữ trên AWS: <br>&emsp; + Amazon  Simple Storage Service (S3) <br>&emsp; + Các tính năng S3 nâng cao<br>&emsp; + Snow Family <br>&emsp; + Storage Gateway <br>&emsp; + RTO/RPO <br>&emsp; + Disater Recovery<br>&emsp; + AWS Backup                                                                                                                | 08/05/2026   | 08/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 2     | - Thực hành triển khai website tĩnh trên S3, thực hiện các kỹ năng quản trị, bảo mật và dự phòng dữ liệu qua việc phân quyền, quản lý phiên bản, sao chép liên vùng <br> - **Thực hành:** <br>&emsp; + Tạo bucket và tải source code website lên <br>&emsp; + Kích hoạt và cấu hình tính năng lưu trữ website tĩnh <br>&emsp; + Cấu hình Block Public Access <br>&emsp; + Cấu hình public object <br>&emsp; + Kiểm Tra hoạt động Website <br>&emsp; + Thực hiện Bucket Versioning <br>&emsp; + Di chuyển Object giữa 2 Budkets<br>&emsp; + Sao chép S3 Object sang region khác(CRR)<br> - Tìm hiểu tăng tốc truy cập bằng CloudFront với cách khắc phục sự cố S3                                                                                         | 09/05/2026   | 09/05/2026      | <https://000057.awsstudygroup.com/> |
| 3     | - Thực hành thiết lập kế hoạch sao lưu và khôi phục tự động cho các tài nguyên AWS bằng AWS Backup, cấu hình thông báo qua AWS SNS để giám sát và đảm bảo an toàn dữ liệu <br> - **Thực hành:** <br>&emsp; + Tạo Backup Plan <br>&emsp; + Cấu hình & thiết lập thông báo <br> &emsp; + Kiểm tra hoạt động sao lưu <br> - Thực hành triển khai AWS File Storage Gateway thiết lập hệ thống File Share, kết nối và đồng bộ dữ liệu liền mạch giữa môi trường On-premise và lưu trữ đám mây Amazon S3<br> - **Thực hành:** <br>&emsp; + Tạo Bucket và EC2 cho Storage Gateway<br>&emsp; + Cấu hình Storage Gateway<br>&emsp; + Cấu hình File Shares<br>&emsp; + Mapping Driver cho Windows                                                                                   | 10/05/2026   | 10/05/2026      | <https://000013.awsstudygroup.com/><br><https://000024.awsstudygroup.com/> |
| 4     | - Thực hành triển khai hệ thống lưu trữ tệp dùng chung hiệu năng cao trên môi trường Windows với Amazon FSx, thực hiện các kỹ năng quản trị nâng cao như chống trùng lặp dữ liệu, shadow copy, phân bổ hạn mức người dùng và mở rộng tài nguyên linh hoạt<br> - **Thực hành:** <br>&emsp; + Tạo môi trường thực hành <br>&emsp; + Tạo một SSD & HDD Multi-AZ file system  <br>&emsp; + Tạo các file share cho Windows File Server <br>&emsp; + Kiểm tra và giám sát hiệu năng <br>&emsp; + Kích hoạt chống dữ liệu trùng lặp <br>&emsp; + Kích hoạt các bản sao shadow cho toàn bộ hệ thống file <br>&emsp; + Quản lý Session người dùng và mở tệp <br>&emsp; + Kích hoạt hạn ngạch bộ nhớ của người dùng <br>&emsp; + Kích hoạt chia sẻ Truy cập liên tục <br>&emsp; + Thực hiện mở rộng khả năng thông lượng <br>&emsp; + Thực hiện mở rộng dung lượng lưu trữ<br> - Tìm hiểu thêm về cách Sử dụng AWS CLI để triển khai FSx trên Windows                                                                                                                                                                                        | 11/05/2026   | 11/05/2026      | <https://000025.awsstudygroup.com/> |
| 5     | - Tìm hiểu về dịch vụ bảo mật trên AWS: <br>&emsp; + Share Responsibility Model<br>&emsp; + Amazon IAM<br>&emsp; +  Amazon Cognito<br>&emsp; + AWS Organization<br>&emsp; + AWS Organization<br>&emsp; + Amazon KMS<br>&emsp; + AWS Security Hub                                                                                                                                                                         | 12/05/2026   | 12/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6     | - Thực hành các thao tác quản trị truy cập cơ bản trên AWS (IAM) thông qua việc thiết lập User, phân nhóm Group, gán Policy và áp dụng cơ chế bảo mật nâng cao bằng cách Switch Role theo nguyên tắc đặc quyền tối thiểu<br> - **Thực hành:** <br>&emsp; + Tạo IAM Group và IAM User <br>&emsp; + Tạo IAM Role và IAM User <br>&emsp; + Chuyển đổi IAM Role<br> - Thực hành phương pháp bảo mật tối ưu để cấp quyền cho ứng dụng truy cập an toàn vào các dịch vụ AWS bằng IAM Role, thay thế hoàn toàn cho việc sử dụng Access Key tiềm ẩn rủi ro lộ lọt dữ liệu<br> - **Thực hành:** <br>&emsp; + Tạo EC2 Intance và S3 Bucket<br>&emsp; + Tạo IAM user và access key <br>&emsp; + Sử dụng access key để cấp quyền cho ứng dụng truy cập vào S3 <br>&emsp; + Tạo và Sử dụng IAM role để cấp quyền truy cập vào S3 cho ứng dụng thay vì access key                                                                                                                                                       | 13/05/2026   | 13/05/2026      | <tps://000048.awsstudygroup.com><br><https://000004.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

* Làm chủ hệ sinh thái lưu trữ lõi trên AWS:
  * Nắm vững kiến trúc, cách vận hành và các tính năng quản trị nâng cao của Amazon S3.

* Giải pháp di chuyển và lưu trữ lai:
  * Nắm bắt giải pháp kết nối, đồng bộ dữ liệu giữa môi trường On-premise và Cloud qua Storage Gateway.
  * Hiểu rõ các phương pháp di chuyển dữ liệu vật lý quy mô lớn bằng AWS Snow Family.

* Chiến lược Bảo vệ dữ liệu & Phục hồi sau thảm họa:
  * Thấu hiểu các chỉ số kinh doanh cốt lõi RTO và RPO
  * Nắm vững các chiến lược Disaster Recovery để đảm bảo tính liên tục cho hệ thống.
  * Hiểu cách thiết lập, quản lý và tự động hóa các bản sao lưu tập trung với AWS Backup.

* Thực hành Lưu trữ & Phân quyền cơ bản với S3:
  * Triển khai thành công static website và thiết lập cơ chế kiểm soát truy cập thông qua Block Public Access và ACL.
  * Thực hiện thao tác quản lý và di chuyển Object giữa các S3 Bucket.

![Static Website](/images/50.png)

* Thực hành Dự phòng & Bảo vệ dữ liệu S3:
  * Áp dụng tính năng Versioning để kiểm soát thay đổi và phòng tránh rủi ro xóa/ghi đè dữ liệu.
  * Cấu hình thành công cơ chế Cross-Region Replication, đảm bảo tính sẵn sàng cao và phục hồi dữ liệu sau thảm họa.

![Bucket Versioning](/images/51.png)
![S3 Replication](/images/52.png)
![S3 Replication](/images/53.png)
![S3 Replication](/images/54.png)
* Nghiên cứu & Tối ưu hóa hệ thống:
  * Tìm hiểu cơ chế hoạt động của Amazon CloudFront trong việc tăng tốc độ phân phối nội dung và giảm độ trễ cho website.
  * Nắm bắt các Best Practices về bảo mật, hiệu suất, tối ưu chi phí và các kỹ thuật khắc phục sự cố S3 phổ biến.

* Thiết lập và tự động hóa sao lưu với AWS Backup:
  * Khởi tạo thành công Backup Plan với quy tắc sao lưu định kỳ và Backup Vault an toàn.
  * Cấu hình gán tài nguyên Resource Assignments tự động thông qua việc sử dụng Tags.

![Backup Plan](/images/55.png)

* Giám sát và cảnh báo an toàn dữ liệu với AWS SNS:
  * Sử dụng thành thạo dòng lệnh AWS CLI để cấu hình và liên kết sự kiện của Backup Vault với SNS Topic.
  * Thiết lập thành công cơ chế tự động gửi email thông báo khi các tiến trình Backup hoặc Restore hoàn tất nhằm đảm bảo khả năng phản ứng nhanh với sự cố.

![Email Notification](/images/56.png)
![Backup completed successfully](/images/57.png)

* Triển khai hạ tầng Hybrid Storage:
  * Khởi tạo thành công máy chủ EC2 sử dụng AMI Storage Gateway chuyên dụng, thiết lập hệ thống tường lửa Security Groups và cấp phát EBS Volume để làm bộ nhớ đệm Cache.
  * Kết nối và tích hợp thành công Storage Gateway với không gian lưu trữ Amazon S3 Bucket.

![Hybrid Storage](/images/58.png)

* Thiết lập và vận hành File Share:
  * Cấu hình thành công giao thức chia sẻ tệp SMB với cơ chế xác thực Guest access phù hợp cho hệ sinh thái Windows.
  * Thực hiện Mapping Driver thành công trên máy On-premise, gắn kết File Share đám mây thành ổ đĩa mạng cục bộ.
  * Nghiệm thu hoàn tất luồng đồng bộ dữ liệu tự động: Tệp tin tạo mới tại máy tính cục bộ lập tức được đẩy và lưu trữ an toàn trên Amazon S3.

![File Share](/images/59.png)
![S3](/images/60.png)

* Kiểm thử và Giám sát hiệu năng FSx for Windows File Server:
  * Thực hiện ánh xạ File Share vào máy chủ Windows và kiểm thử Read/Write performance bằng công cụ DiskSpd.
  * Giám sát qua CloudWatch Dashboard và thiết lập High Throughput Alarm.

![DiskSpd](/images/61.png)
![High Throughput Alarm](/images/63.png)

* Tối ưu hóa và Dự phòng dữ liệu:
  * Kích hoạt Data Deduplication để tiết kiệm dung lượng.
  * Triển khai Shadow Copies hỗ trợ tính năng Restore previous versions.

![Shadow Copies](/images/62.png)

* Quản trị truy cập và Phân bổ tài nguyên:
  * Quản lý User Sessions và Open Files qua giao diện và PowerShell.
  * Thiết lập User Quotas kiểm soát hạn mức lưu trữ người dùng.
  * Cấu hình Continuously Available Share cho các ứng dụng như SQL Server.

* Mở rộng hệ thống và nghiên cứu:
  * Thực hiện nâng cấp Storage Capacity và Throughput Capacity không gián đoạn.
  * Nghiên cứu tham khảo AWS CLI cho quá trình tự động hóa.

* Mô hình bảo mật cốt lõi:
  * Nắm vững Mô hình Trách nhiệm Chia sẻ (Shared Responsibility Model) phân định rõ vai trò giữa AWS và người dùng.

* Quản trị Định danh & Truy cập:
  * Hiểu rõ Amazon IAM để kiểm soát phân quyền tài nguyên nội bộ AWS.
  * Nắm bắt Amazon Cognito để quản lý xác thực người dùng cho các ứng dụng web/mobile.

* Quản trị tập trung & Giám sát an ninh:
  * Tìm hiểu AWS Organizations giúp thiết lập và quản lý chính sách bảo mật cho nhiều tài khoản.
  * Hiểu cơ chế hoạt động của AWS Security Hub để theo dõi trạng thái và cảnh báo an ninh toàn diện.

* Mã hóa & Bảo vệ dữ liệu:
  * Nắm vững cơ chế tạo và quản lý vòng đời khóa mã hóa an toàn với Amazon KMS.

* Quản trị định danh và phân quyền cơ bản:
  * Thiết lập thành công cấu trúc quản lý tập trung thông qua việc khởi tạo IAM Group và áp dụng các IAM Policy phù hợp.
  * Tạo và quản lý thông tin đăng nhập IAM User an toàn, loại bỏ hoàn toàn việc sử dụng tài khoản Root cho các tác vụ vận hành hệ thống.

* Bảo mật nâng cao và kiểm soát đặc quyền:
  * Khởi tạo IAM Role với cấu hình Trusted Entity chuẩn xác nhằm cung cấp các phiên truy cập tạm thời.
  * Thiết lập thành công Inline Policy gắn trực tiếp cho người dùng, cấp quyền sts:AssumeRole một cách chặt chẽ.
  * Thực hành thành thạo kỹ thuật Switch Role, cho phép người dùng có quyền hạn thấp tạm thời nâng quyền quản trị hệ thống, tuân thủ tuyệt đối nguyên tắc Least Privilege.

![Least Privilege](/images/64.png)
![Switch Role](/images/65.png)

* Nhận diện rủi ro bảo mật (Access Key):
  * Kiểm thử thành công việc kết nối ứng dụng tới S3 thông qua Access Key và Secret Access Key.
  * Nhận thức rõ rủi ro bảo mật nghiêm trọng của phương pháp cũ khi thông tin xác thực tĩnh bị lập trình cứng (hardcode) trực tiếp vào mã nguồn.

* Triển khai bảo mật tối ưu (IAM Role):
  * Thiết lập thành công IAM Role (với định dạng Trusted Entity là EC2) và gắn policy AmazonS3FullAccess.
  * Áp dụng Role cho EC2 Instance, giúp ứng dụng thực hiện upload file lên S3 an toàn tuyệt đối mà không cần lưu trữ bất kỳ thông tin xác thực nào, loại bỏ hoàn toàn nguy cơ lộ lọt dữ liệu.

![Application Access Key](/images/66.png)
![Application IAM Role](/images/67.png)