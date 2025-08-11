---
title : "Các bước tạo RDS"
date: 2025-06-18
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---


# Tạo RDS PostgreSQL

1. RDS → **Create database**
2. Engine: **PostgreSQL**, Template: **Free tier**
3. DB instance identifier: `ctdemo-pg`
4. Master username: `postgres`, password: đặt mạnh
5. Instance class: `db.t3.micro`, Storage: GP3 (20GB)
6. **Connectivity**:
   - Chọn VPC của EC2
   - DB subnet group: default (hoặc subnet riêng)
   - Public access: **No**
   - VPC SG: chọn SG cho RDS, **mở 5432 từ SG của EC2**
7. Tạo database và đợi **Available**.

![Create RDS](github.io.workshop/images/rds/001.png)
![Create RDS](github.io.workshop/images/rds/002.png)
![Create RDS](github.io.workshop/images/rds/003.png)
![Create RDS](github.io.workshop/images/rds/004.png)
![Create RDS](github.io.workshop/images/rds/005.png)
![Create RDS](github.io.workshop/images/rds/006.png)

=> Chọn Clone nếu không muốn dùng dịch vụ phí
![Create RDS](github.io.workshop/images/rds/007.png)
![Create RDS](github.io.workshop/images/rds/008.png)
### Kết nối từ EC2
```bash
sudo dnf install -y postgresql15
psql "host=<RDS-ENDPOINT> port=5432 user=postgres dbname=postgres password=<PASS>"

