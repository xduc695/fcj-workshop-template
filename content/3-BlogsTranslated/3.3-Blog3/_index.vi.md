---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# BỨT PHÁ GIỚI HẠN 90 NGÀY CỦA EC2 CAPACITY MANAGER VỚI AMAZON ATHENA

Trong quản trị hạ tầng AWS quy mô lớn, việc kiểm soát và dự phóng chi phí máy chủ luôn là bài toán hóc búa đối với các doanh nghiệp. Để hỗ trợ các kỹ sư theo dõi tài nguyên, Amazon EC2 Capacity Manager mang lại cái nhìn tập trung về tình hình sử dụng dung lượng (On-Demand, Spot, ODCR) xuyên suốt các tài khoản và Region trong toàn bộ tổ chức.

Tuy nhiên, một điểm nghẽn lớn khi vận hành thực tế là: Hệ thống chỉ lưu trữ tối đa 90 ngày dữ liệu lịch sử trên AWS Management Console. Điều này gây rất nhiều khó khăn khi đội ngũ FinOps cần phân tích xu hướng dài hạn theo năm, lập kế hoạch ngân sách hoặc đánh giá hiệu quả của các gói đặt trước dung lượng (ODCR) đã mua từ trước. Bài viết này tổng hợp chi tiết kiến trúc, quy trình tự động hóa phân vùng và các kịch bản SQL thực tế nhằm làm chủ dữ liệu hạ tầng dài hạn.

---

## 1. Các ưu điểm cốt lõi của giải pháp

Kiến trúc triển khai tập trung tối ưu hóa hệ thống dựa trên hai khía cạnh quan trọng: khả năng lưu trữ dài hạn và năng lực truy vấn dữ liệu thông minh trên quy mô lớn.

- **Vượt qua giới hạn lưu trữ dữ liệu:** Giải pháp cho phép tự động đóng gói toàn bộ dữ liệu hạ tầng (On-Demand, Spot, ODCR) hàng giờ (`Hourly`) thành file nén tối ưu định dạng Parquet (Snappy), giúp doanh nghiệp lưu trữ vĩnh viễn trên Amazon S3 phục vụ phân tích xu hướng theo năm.
- **Tự động hóa với Partition Projection:** Loại bỏ hoàn toàn việc vận hành các công cụ quét dữ liệu (AWS Glue Crawler) thủ công hàng ngày để cập nhật metadata. Bằng cách thiết lập thuộc tính `TBLPROPERTIES` trong Athena, hệ thống tự động tính toán và nhận diện các phân vùng thư mục ngày/giờ mới ngay tại thời điểm truy vấn.
- **Bảo mật phân tách tài nguyên qua Bucket Policy:** Áp dụng các mệnh đề điều kiện (`Condition`) khắt khe như `aws:SourceAccount` và `ArnLike` gắn với đường dẫn export cụ thể, đảm bảo chỉ cấp quyền ghi dữ liệu tự động cho duy nhất service của EC2 Capacity Manager theo nguyên tắc đặc quyền tối thiểu (Least Privilege).

---

## 2. Quy trình hoạt động của hệ thống

Luồng xử lý dữ liệu của giải pháp được chia tách rõ ràng thành hai giai đoạn độc lập thông qua cấu hình dịch vụ AWS:

- **Khi xuất dữ liệu (Data Export):** EC2 Capacity Manager tiếp nhận cấu hình, định kỳ hàng giờ tiến hành quét, tổng hợp số liệu sử dụng tài nguyên của toàn bộ các tài khoản/Region rồi nén và đẩy trực tiếp về S3 Bucket theo cấu trúc phân vùng thư mục ngày/giờ (`y=YYYY/m=MM/d=DD/h=HH`).
- **Khi truy vấn (Querying):** Kỹ sư FinOps thực thi câu lệnh SQL trên Amazon Athena. Lúc này, Athena không quét toàn bộ bucket mà dựa trên các tham số cấu hình Partition Projection để tính toán chính xác đường dẫn thư mục cần đọc, giúp trả về kết quả phân tích chỉ trong vài giây với lượng dữ liệu quét tối thiểu.

---

![EC2 Capacity Manager](/images/105.png)
## 3. Lựa chọn công nghệ và phạm vi lưu trữ

| Thành phần hệ thống | Công nghệ sử dụng | Vai trò trong kiến trúc |
| :--- | :--- | :--- |
| **Data Collection** | EC2 Capacity Manager | Thu thập dữ liệu sử dụng hạ tầng (On-Demand, Spot, ODCR) tập trung |
| **Data Storage** | Amazon S3 | Kho lưu trữ dữ liệu lịch sử dài hạn dưới định dạng nén Parquet (Snappy) |
| **Metadata Store** | AWS Glue Data Catalog | Lưu trữ định nghĩa cấu trúc bảng (Schema) để Amazon Athena tham chiếu |
| **Data Analytics** | Amazon Athena | Thực thi các câu lệnh SQL nâng cao để lọc và trích xuất báo cáo FinOps |

---

## 4. Các kịch bản tối ưu chi phí (FinOps) khi triển khai thực tế

Giải pháp mở ra năng lực tối ưu hóa chi phí hạ tầng chuyên sâu thông qua 3 kịch bản truy vấn SQL thực tế được áp dụng trực tiếp trên hệ thống:

### Săn tìm các gói ODCR lãng phí
Hệ thống sử dụng các hàm toán học nâng cao (`CAST`, `ROUND`) để lọc và định vị chính xác mã `reservationid` của các gói đặt trước dung lượng hoạt động kém hiệu quả (hiệu suất sử dụng < 50%) nhưng vẫn bị tính tiền, tính toán ra số tiền thâm hụt hàng giờ (`wasted_cost_usd`) để doanh nghiệp kịp thời hủy hoặc điều chuyển tài nguyên.

### Nhận diện quy luật tải đỉnh (Peak Usage)
Khai thác tập dữ liệu thuộc nhóm `Instance Usage` để tính toán lượng máy chủ chạy thực tế trung bình theo từng khung giờ trong ngày (từ 00h đến 23h). Quy trình phân tích này giúp xác định chính xác thời điểm hệ thống chạm ngưỡng cao điểm, làm cơ sở để đưa ra chiến lược mua sắm gói tài nguyên hợp lý.

### Chia sẻ tài nguyên nội bộ thông minh
Truy vấn đi sâu vào dữ liệu ở cấp độ khu vực hạ tầng vật lý Availability Zone (`az-id`) để tìm ra vùng nào đang thừa công suất. Số liệu này giúp doanh nghiệp chủ động điều phối, chia sẻ dung lượng trống cho các đội ngũ (team) khác dùng chung và tiến hành dọn dẹp sạch sẽ toàn bộ tài nguyên thử nghiệm sau khi hoàn tất.

---

![Athena SQL Query Results](/images/103.png)
## 5. Lời kết

Sự kết hợp giữa EC2 Capacity Manager, S3 và Athena mang lại một giải pháp quản trị và tối ưu chi phí hạ tầng toàn diện vượt qua giới hạn lưu trữ thông thường. Phương án tiếp cận này giúp các doanh nghiệp chuyển dịch từ thế bị động giải quyết chi phí phát sinh sang chủ động làm chủ dữ liệu, tối ưu hóa hạ tầng và nâng cao hiệu quả tài chính trên đám mây AWS.

Bài viết gốc: https://aws.amazon.com/vi/blogs/compute/maximize-amazon-ec2-capacity-reservations-with-capacity-manager-data-exports/