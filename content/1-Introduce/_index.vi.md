---
title : "Giới thiệu"
date: 2025-06-18
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
# Tổng quan

Workshop này hướng dẫn triển khai một ứng dụng demo trên AWS gồm:
- EC2: máy chủ ứng dụng.
- RDS (PostgreSQL): cơ sở dữ liệu được quản lý.
- S3: lưu trữ log/artefacts.
- SES: dịch vụ gửi email (SMTP).

## Kiến trúc demo
1. EC2 chạy ứng dụng Spring Boot (hoặc app bất kỳ).
2. EC2 kết nối đến RDS PostgreSQL trong cùng VPC.
3. Ứng dụng ghi log/artefacts lên S3.
4. Ứng dụng gửi email qua Amazon SES (SMTP).

## Cấu trúc front-end Website
![Launch EC2](/images/pj/001.png)

## Cấu trúc Back-end Website
![Launch EC2](/images/pj/002.png)
## Models
![Launch EC2](/images/pj/003.png)
## Controller
![Launch EC2](/images/pj/004.png)
## DTO
![Launch EC2](/images/pj/005.png)
## Repository
![Launch EC2](/images/pj/006.png)
## Sercurity
![Launch EC2](/images/pj/007.png)
## Service
![Launch EC2](/images/pj/008.png)