---
title : "Cấu hình Routing cho NAT Gateway"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

Để đảm bảo các Fargate Tasks chạy trong Private Subnets có thể kết nối Outbound ra ngoài Internet để kéo Docker Images từ ECR và đẩy logs lên CloudWatch, chúng ta cần cấu hình NAT Gateway vào Route Table của Private Subnets.

---

### Các bước cấu hình Private Route Table:

1. Tại dịch vụ **VPC**, click chọn **Route Tables** ở menu bên trái.
2. Tìm và click chọn **Private Route Table** (là Route Table đang liên kết với 2 Private Subnets của bạn).
3. Nhìn xuống khu vực cấu hình bên dưới, chọn tab **Routes** -> nhấp vào nút **Edit routes**.
4. Kiểm tra xem đã có route này chưa:
   - **Destination**: `0.0.0.0/0`
   - **Target**: Chọn **NAT Gateway** -> chọn đúng ID NAT Gateway vừa được tạo tự động dạng `pg-nat...`.
5. Nếu chưa có, click chọn **Add route** để thêm thủ công:
   - **Destination**: Nhập `0.0.0.0/0`.
   - **Target**: Chọn **NAT Gateway** và chọn ID NAT Gateway tương ứng.
6. Nhấp nút **Save changes** để lưu lại.

![Xác nhận NAT route](/images/h15.png)
