+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

### Bước 1: Xóa các phiên EC2
Vào **AWS EC2 Console** → Chọn các instance bạn đã tạo → **Actions → Instance State → Terminate**.

### Bước 2: Xóa Security Group và Key Pair
- Xóa Security Group nếu không còn dùng.
- Xóa Key Pair để tránh sử dụng lại.

### Bước 3: Xóa RDS
- Vào **AWS RDS Console** → Chọn database đã tạo.
- Chọn **Actions → Delete**.
- Nếu muốn xóa cả snapshot, bỏ chọn **Create final snapshot**.

### Bước 4: Xóa S3 Bucket
Nếu đã tạo S3 bucket để lưu log, vào **AWS S3 Console** → Chọn bucket → **Delete**.

### Bước 5: Xóa SES Identity và User
- Vào **AWS SES Console** → Chọn **Verified Identities** → Xóa email hoặc domain.
- Vào **AWS IAM Console** → Xóa user/role đã tạo cho SES.

### Bước 6: Xóa IAM Role (nếu chưa xóa ở bước trên)
- Vào **AWS IAM Console** → Chọn role đã tạo → **Delete**.