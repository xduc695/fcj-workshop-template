---
title: "Worklog Tuần 10"
date: 2026-06-19
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10:

* Tìm hiểu quy trình và thực hành triển khai hệ thống sao lưu, phục hồi thảm họa trên Amazon EKS bằng Velero.
* Tổng hợp kiến thức cấu hình Velero trên Amazon EKS thành bài viết kỹ thuật chia sẻ lên cộng đồng AWS Vietnam.
* Tìm hiểu quy trình và thực hành triển khai hệ thống lưu trữ dữ liệu dung lượng EC2 dài hạn, phục vụ phân tích và tối ưu hóa chi phí (FinOps) bằng Amazon S3 và Amazon Athena.
* Tổng hợp giải pháp cấu hình Data Export trên EC2 Capacity Manager kết hợp Amazon Athena thành bài viết kỹ thuật chia sẻ lên cộng đồng AWS Vietnam.
* Tìm hiểu Redis nhằm tối ưu tốc độ phản hồi, phân tán dữ liệu và nâng cao năng lực chịu tải cho hệ thống.
* Tìm hiểu Transactions phân tán nhằm bảo đảm tính nhất quán dữ liệu liên dịch vụ trong kiến trúc Microservices.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Tìm hiểu quy trình và tiến hành thực hành cấu hình hệ thống sao lưu, phục hồi thảm họa (Disaster Recovery) trên Amazon EKS bằng Velero, nhằm xây dựng giải pháp bảo mật toàn vẹn dữ liệu cho các ứng dụng có trạng thái (Stateful), giúp tự động hóa việc lưu trữ cấu hình logic lên Amazon S3 và chụp ảnh đĩa vật lý dưới dạng Amazon EBS Snapshots <br> - **Thực hành:** <br>&emsp; + Khởi tạo Amazon S3 Bucket phục vụ lưu trữ tập trung dữ liệu sao lưu cấu hình cụm <br>&emsp; + Tạo IAM Policy, IAM Role chuyên dụng và cấu hình EKS Pod Identity Association để phân quyền tối thiểu (Least Privilege) cho Velero <br>&emsp; + Cài đặt Snapshot Controller add-on trên cụm EKS và thiết lập VolumeSnapshotClass cho driver Amazon EBS <br>&emsp; + Triển khai Velero Server bằng Helm Chart kết hợp áp dụng custom ClusterRole nhằm siết chặt bảo mật hệ thống <br>&emsp; + Triển khai ứng dụng mẫu (Stateful App) gắn ổ đĩa bền vững gp3 trong namespace myprimary để tạo dữ liệu thử nghiệm <br>&emsp; + Cấu hình và thực thi Velero Backup Custom Resource để tiến hành sao lưu đồng bộ toàn bộ tài nguyên <br>&emsp; + Áp dụng Velero Restore Custom Resource kết hợp tính năng namespaceMapping để khôi phục toàn vẹn dữ liệu sang namespace myrestore <br>&emsp; + Kiểm tra luồng dữ liệu sau khôi phục, xử lý các lỗi đặc thù trên môi trường Windows CMD, lỗi kẹt Pod Pending và tiến hành dọn dẹp sạch sẽ toàn bộ tài nguyên AWS sau khi hoàn tất.                                                                                             | 19/06/2026   | 19/06/2026      | <https://aws.amazon.com/vi/blogs/containers/back-up-and-restore-your-amazon-eks-cluster-resources-using-velero/> |
| 2   | - Tổng hợp kiến thức về cấu hình hệ thống sao lưu và khôi phục thảm họa (Disaster Recovery) trên Amazon EKS bằng Velero để xây dựng bài chia sẻ kỹ thuật lên cộng đồng AWS Vietnam: <br>&emsp; + Tóm tắt nội dung cốt lõi của bài AWS Blog về giải pháp sao lưu tài nguyên cụm EKS và dữ liệu ổ đĩa bền vững bằng Velero <br>&emsp; + Hệ thống lại quy trình hoạt động của tiến trình Backup/Restore: đóng gói tài nguyên logic lên Amazon S3 và chụp ảnh đĩa vật lý dưới dạng Amazon EBS Snapshots <br>&emsp; + Phân tích vai trò và cơ chế phối hợp của các thành phần hệ thống: Velero Controller, Amazon S3, Amazon EBS Snapshots, EKS Pod Identity và Custom ClusterRole <br>&emsp; + Tổng hợp chi tiết các bước thực hành thực tế, luồng dịch chuyển dữ liệu chéo namespace và giải pháp xử lý các lỗi phát sinh đặc thù (cú pháp trên Windows CMD, lỗi kẹt Pod Pending do nodeSelector) <br>&emsp; + Biên soạn bài viết chia sẻ theo hướng thực tế, súc tích, cấu trúc phân cấp rõ ràng và phù hợp với văn phong thảo luận kỹ thuật của cộng đồng                                            | 20/06/2026   | 20/06/2026      | <https://aws.amazon.com/vi/blogs/containers/back-up-and-restore-your-amazon-eks-cluster-resources-using-velero/> |
| 3   | - Tìm hiểu quy trình và tiến hành thực hành cấu hình hệ thống lưu trữ dữ liệu dung lượng lịch sử dài hạn trên Amazon EC2 bằng Capacity Manager và Amazon Athena, nhằm xây dựng giải pháp tối ưu hóa chi phí (FinOps) xuyên suốt các tài khoản và tổ chức, giúp tự động hóa việc xuất log định dạng nén Parquet lên Amazon S3 và truy vấn thông minh bằng ngôn ngữ SQL. <br> - **Thực hành:** <br>&emsp; + Khởi tạo Amazon S3 Bucket phục vụ lưu trữ tập trung dữ liệu dung lượng máy chủ theo cấu trúc ngày/giờ <br>&emsp; + Tạo S3 Bucket Policy chuyên dụng nhằm cấp quyền ghi nhận dữ liệu tự động (Write Access) cho dịch vụ EC2 Capacity Manager <br>&emsp; + Thiết lập luồng tự động xuất dữ liệu (Data Export) hàng giờ định dạng Parquet thông qua giao diện AWS Console và AWS CLI <br>&emsp; + Khởi tạo Cơ sở dữ liệu và Cấu hình External Table trên Amazon Athena sử dụng tính năng Chiếu phân vùng (Partition Projection) để tự động nhận diện dữ liệu mới <br>&emsp; + Thực thi câu lệnh SQL nâng cao để săn tìm và định vị các gói đặt trước dung lượng (ODCR) có hiệu suất thấp gây lãng phí ngân sách <br>&emsp; + Triển khai truy vấn phân tích quy luật tải đỉnh (Peak Usage Patterns) theo từng khung giờ trong ngày để tối ưu chiến lược mua sắm tài nguyên <br>&emsp; + Truy vấn chi tiết cấp độ Availability Zone (AZ ID) để xác định dung lượng trống phục vụ điều phối và chia sẻ tài nguyên dùng chung giữa các đội ngũ <br>&emsp; + Kiểm tra luồng dữ liệu thực tế, hiệu chỉnh điều kiện lọc thời gian thích hợp và tiến hành dọn dẹp sạch sẽ (Clean up) toàn bộ tài nguyên nhằm tránh phát sinh chi phí ngoài ý muốn. | 21/06/2026   | 21/06/2026      | <https://aws.amazon.com/vi/blogs/compute/maximize-amazon-ec2-capacity-reservations-with-capacity-manager-data-exports/> |
| 4   | - Tổng hợp kiến thức về cấu hình hệ thống xuất và phân tích dữ liệu dung lượng lịch sử dài hạn trên Amazon EC2 bằng Capacity Manager và Amazon Athena để xây dựng bài chia sẻ kỹ thuật lên cộng đồng AWS Vietnam: <br>&emsp; + Tóm tắt nội dung cốt lõi của bài AWS Blog về giải pháp lưu trữ và phân tích xu hướng sử dụng dung lượng máy chủ vượt qua giới hạn 90 ngày của AWS Console <br>&emsp; + Hệ thống lại quy trình hoạt động của luồng dữ liệu tự động: xuất file nén định dạng Parquet (Snappy) hàng giờ lên Amazon S3 và thực thi truy vấn SQL qua Amazon Athena <br>&emsp; + Phân tích vai trò và cơ chế phối hợp của các thành phần hệ thống: EC2 Capacity Manager, S3 Bucket Policy, Amazon Athena và tính năng chiếu phân vùng thông minh Partition Projection <br>&emsp; + Tổng hợp chi tiết các kịch bản thực tế dựa trên các câu lệnh SQL nâng cao để xử lý bài toán FinOps (săn tìm ODCR lãng phí, nhận diện quy luật tải đỉnh Peak Usage và điều phối dung lượng trống theo Availability Zone) <br>&emsp; + Biên soạn bài viết chia sẻ theo hướng thực tế, ngắn gọn, súc tích, cấu trúc phân cấp rõ ràng, đính kèm link tài liệu gốc và phù hợp với văn phong thảo luận kỹ thuật của cộng đồng.                  | 22/06/2026   | 22/06/2026      | <https://aws.amazon.com/vi/blogs/compute/maximize-amazon-ec2-capacity-reservations-with-capacity-manager-data-exports/> |
| 5   | - Nghiên cứu lý thuyết về Redis và các giải pháp tối ưu hiệu năng, chịu tải cho hệ thống: <br>&emsp; + Tìm hiểu kiến trúc lưu trữ trên RAM của Redis và các chiến lược Caching (như Cache-Aside) để tối ưu tốc độ phản hồi. <br>&emsp; + Nghiên cứu cơ chế phân tán dữ liệu, quản lý Session và chống trùng lặp dữ liệu (Idempotency) trong môi trường phân tán. <br>&emsp; + Tìm hiểu nguyên lý hoạt động của Distributed Lock (Khóa phân tán) thông qua thư viện Redisson để kiểm soát tranh chấp tài nguyên.                                                                                         | 23/06/2026   | 23/06/2026      |              
| 6   | - Nghiên cứu lý thuyết về Transactions phân tán và các giải pháp đảm bảo nhất quán dữ liệu: <br>&emsp; + Tìm hiểu sự khác biệt giữa Local Transaction và Distributed Transaction, lý do hạn chế sử dụng giao thức 2PC (Two-Phase Commit). <br>&emsp; + Nghiên cứu nguyên lý vận hành của Saga Pattern thông qua hai trường phái: Tự phát (Choreography) và Điều phối (Orchestration). <br>&emsp; + Tìm hiểu cơ chế thiết lập Giao dịch bù trừ (Compensating Transaction) để tự động hoàn trả dữ liệu về trạng thái đúng khi xảy ra lỗi.                                                                                         | 24/06/2026   | 24/06/2026      |  
                                                                                                 


### Kết quả đạt được tuần 10:

* Triển khai và thực hiện thành công quy trình sao lưu (Backup) đồng bộ cụm EKS bằng Velero:

  * Cấu hình thành công tiến trình Velero tự động đóng gói toàn bộ tài nguyên cấu hình logic (Deployments, PVCs, Secrets...) thành file nén lưu trữ an toàn trên Amazon S3 Bucket.
  * Kích hoạt thành công hệ thống Snapshot Controller gọi API của AWS để đóng băng và chụp ảnh đĩa vật lý lưu dưới dạng Amazon EBS Snapshots cho phân vùng đĩa bền vững `gp3`.
  * Xác minh trạng thái tiến trình sao lưu hoàn thành xuất sắc thông qua kiểm tra thuộc tính thuộc Phase của Velero Backup Custom Resource.

![Velero Backup Completed](/images/100.png)

* Khôi phục thành công toàn vẹn dữ liệu ứng dụng có trạng thái sang một không gian tên độc lập bằng tính năng Mapping:

  * Sử dụng thành công Velero Restore Custom Resource kết hợp cơ chế `namespaceMapping` để dịch chuyển và tái thiết lập toàn bộ tài nguyên từ namespace gốc sang namespace mới.
  * AWS tự động đọc thông tin snapshot cũ từ tiến trình backup trước đó, khởi tạo thành công một ổ đĩa `gp3` mới hoàn toàn và tự động gắn (mount) trực tiếp vào máy chủ Worker Node mới.
  * Kiểm chứng dữ liệu thực tế bên trong Pod sau khi khôi phục, đảm bảo tệp log lịch sử được giữ nguyên vẹn và ứng dụng tiếp tục ghi dữ liệu nối tiếp thành công.


* Cấu hình thành công cơ chế quản lý định danh và siết chặt bảo mật hạ tầng bằng quyền hạn tối thiểu:

  * Thiết lập thành công mối quan hệ tin cậy ngắn hạn giữa tài khoản dịch vụ Kubernetes và AWS thông qua tính năng EKS Pod Identity Association, loại bỏ hoàn toàn việc sử dụng thông tin xác thực tĩnh.
  * Thay thế thành công quyền truy cập hệ thống mặc định bằng việc triển khai ClusterRole tùy chỉnh thu hẹp, chỉ cấp quyền hạn vừa đủ cho Velero tương tác với các apiGroups thực sự cần thiết.

![EKS Pod Identity Association](/images/101.png)

* Hoàn thành việc tổng hợp kiến thức về cấu hình hệ thống sao lưu và khôi phục thảm họa (Disaster Recovery) trên Amazon EKS bằng Velero:

  * Nắm vững nội dung cốt lõi của bài AWS Blog về cơ chế hoạt động của Velero và vai trò của giải pháp trong quản trị vận hành cụm Kubernetes.
  * Hệ thống lại được toàn bộ luồng hoạt động đồng bộ: từ tiến trình Velero đóng gói tài nguyên logic lên Amazon S3 đến việc kích hoạt Snapshot Controller chụp ảnh đĩa vật lý Amazon EBS Snapshots.
  * Phân tích được vai trò và cơ chế phối hợp của các thành phần trong kiến trúc bảo mật: Velero Controller, Amazon S3, EBS Snapshots, EKS Pod Identity và Custom ClusterRole theo nguyên tắc phân quyền tối thiểu (Least Privilege).
  * Tổng hợp được chi tiết các bước thực hiện thực tế, cơ chế dịch chuyển dữ liệu chéo namespace qua tính năng `namespaceMapping`, các lỗi thường gặp (cú pháp trên Windows CMD, kẹt Pod do `nodeSelector`) và cách xử lý triệt để.
  * Biên soạn được bài viết chia sẻ kỹ thuật ngắn gọn, súc tích, có cấu trúc phân cấp rõ ràng và phù hợp với văn phong thảo luận của cộng đồng AWS Vietnam.

* Triển khai và thực hiện thành công quy trình xuất dữ liệu lịch sử dung lượng máy chủ tập trung bằng EC2 Capacity Manager:

  * Cấu hình thành công tiến trình Capacity Manager tự động đóng gói dữ liệu sử dụng hạ tầng (On-Demand, Spot, ODCR) hàng giờ thành file nén tối ưu định dạng Parquet (Snappy) đẩy về Amazon S3 Bucket.
  * Thiết lập và phân quyền thành công S3 Bucket Policy chuyên dụng, đảm bảo dịch vụ có thể ghi dữ liệu tự động theo đúng nguyên tắc bảo mật và phân tách tài nguyên.
  * Xác minh trạng thái tiến trình xuất dữ liệu hoàn thành xuất sắc thông qua kiểm tra trường LatestDeliveryStatus trả về giá trị delivered bằng AWS CLI.

![Capacity Manager Data Export Delivered](/images/102.png)

* Khởi tạo thành công cơ sở dữ liệu và tự động hóa nhận diện phân vùng dữ liệu dài hạn trên Amazon Athena:

  * Thiết lập thành công Cơ sở dữ liệu capacity_manager_db và khởi tạo External Table ánh xạ cấu trúc dữ liệu dạng thư mục từ Amazon S3.
  * Áp dụng thành công tính năng Chiếu phân vùng (Partition Projection) thông qua việc định nghĩa các thuộc tính TBLPROPERTIES, giúp Athena tự động tính toán và hiển thị các phân vùng ngày/giờ mới mà không cần chạy Glue Crawler thủ công.

* Thực thi thành công các kịch bản truy vấn phân tích dữ liệu chuyên sâu phục vụ tối ưu hóa chi phí (FinOps):

  * Sử dụng thành công câu lệnh SQL nâng cao để lọc và săn tìm chính xác các gói đặt trước dung lượng (ODCR) hoạt động kém hiệu quả (utilization < 50%), tính toán số tiền lãng phí thực tế (wasted_cost_usd) để ra quyết định hạ cấp tài nguyên.
  * Khai thác thành công dữ liệu Instance Usage để bóc tách quy luật tải đỉnh (Peak Usage) theo từng khung giờ, làm cơ sở tối ưu hóa chiến lược mua sắm máy chủ cho doanh nghiệp.
  * Định vị thành công phần dung lượng trống chi tiết ở cấp độ Availability Zone (AZ ID) để chia sẻ, điều phối tài nguyên dùng chung giữa các đội ngũ và tiến hành dọn dẹp sạch sẽ toàn bộ tài nguyên thử nghiệm sau khi hoàn tất.

![Athena SQL Query Results](/images/103.png)

* Hoàn thành việc tổng hợp kiến thức về cấu hình hệ thống xuất và phân tích dữ liệu dung lượng lịch sử dài hạn trên Amazon EC2 bằng Capacity Manager và Amazon Athena:

  * Nắm vững nội dung cốt lõi của bài AWS Blog về giải pháp bứt phá giới hạn lưu trữ 90 ngày của AWS Console và vai trò của luồng dữ liệu tự động trong quản trị vận hành, tối ưu chi phí (FinOps).
  * Hệ thống lại được toàn bộ luồng hoạt động đồng bộ: từ tiến trình EC2 Capacity Manager tự động xuất file nén định dạng Parquet (Snappy) lên Amazon S3 đến việc Amazon Athena thực thi truy vấn trực tiếp.
  * Phân tích được vai trò và cơ chế phối hợp của các thành phần trong kiến trúc tối ưu: EC2 Capacity Manager, S3 Bucket Policy, Amazon Athena và tính năng tự động hóa cấu trúc bảng bằng Partition Projection.
  * Tổng hợp được chi tiết các bước thực hiện thực tế, cơ chế tối ưu FinOps thông qua 3 kịch bản truy vấn SQL nâng cao (săn tìm ODCR lãng phí, nhận diện quy luật tải đỉnh Peak Usage, điều phối tài nguyên theo AZ ID) và quy trình dọn dẹp hệ thống chuẩn xác.
  * Biên soạn được bài viết chia sẻ kỹ thuật ngắn gọn, súc tích, cấu trúc phân cấp rõ ràng, đính kèm link tài liệu gốc và phù hợp với văn phong thảo luận của cộng đồng AWS Vietnam.

* Nghiên cứu giải pháp tối ưu hiệu năng và chịu tải với Redis:
  * Nắm vững kiến trúc lưu trữ dữ liệu trên bộ nhớ RAM của Redis, hiểu rõ lý do giúp hệ thống đạt tốc độ phản hồi siêu nhanh (dưới miligiây) và khả năng chịu tải hàng trăm ngàn request/giây.
  * Làm chủ nguyên lý vận hành của chiến lược bộ nhớ đệm Cache-Aside Pattern để giảm tải tối đa cho cơ sở dữ liệu quan hệ (PostgreSQL) phía sau.
  * Hiểu sâu về cơ chế thiết lập thời gian sống của dữ liệu (TTL - Time To Live) và các chính sách giải phóng bộ nhớ (Eviction Policies) khi Redis bị đầy bộ nhớ.

* Hệ thống hóa lý thuyết kiểm soát giao dịch phân tán với Redis:
  * Định hình được giải pháp quản lý Session tập trung và cơ chế kiểm soát trùng lặp yêu cầu (Idempotency Check) để chống spam API trong hệ thống ngân hàng.
  * Nắm vững nguyên lý hoạt động của Khóa phân tán (Distributed Lock) thông qua thư viện Redisson, giải quyết triệt để bài toán tranh chấp tài nguyên (Race Condition) khi nhiều luồng cùng thao tác trên một tài khoản.

* Nghiên cứu giải pháp nhất quán dữ liệu liên dịch vụ với Distributed Transactions:
  * Nắm vững bản chất của bài toán nhất quán sau cùng (Eventual Consistency) trong hệ thống ngân hàng phân tán, hiểu rõ lý do tại sao các cơ chế khóa đồng bộ truyền thống không thể đáp ứng khi hệ thống chịu tải cao.
  * Làm chủ tư duy thiết kế cấu trúc Saga Pattern, định hình được cách phối hợp các dịch vụ (như trừ tiền bên A và cộng tiền bên B) thông qua luồng sự kiện phi đồng bộ.
  * Hiểu sâu về cơ chế định danh giao dịch (Global Transaction ID) và cách thiết kế các hàm bù trừ (Rollback bằng logic) giúp hệ thống tự phục hồi dữ liệu về trạng thái cân bằng nếu một mắt xích trong chuỗi giao dịch bị thất bại.