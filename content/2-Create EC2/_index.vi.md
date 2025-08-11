---
title : "Các bước tạo EC2"
date: 2025-06-18
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

# Tạo EC2

### Bước 1: Launch instance
- AMI: **Amazon Linux 2023**
- Instance type: **t2.micro** (Free tier)
- Key pair: tạo/tải file `.pem`
- Security Group: mở **22/TCP** (giới hạn IP của bạn)
- Launch

![Launch EC2](github.io.workshop/images/ec2/001.png)


### Tạo key pair

![Launch EC2](github.io.workshop/images/ec2/002.png)

### Cấu hình mạng

![Launch EC2](github.io.workshop/images/ec2/003.png)
![Launch EC2](github.io.workshop/images/ec2/004.png)
![Launch EC2](github.io.workshop/images/ec2/005.png)


### Bước 2: SSH vào EC2

![Launch EC2](github.io.workshop/images/ec2/006.png)
```bash
chmod 400 your-key.pem
ssh -i your-key.pem ec2-user@<EC2-Public-IP>
```

### Bước 3 : Cài Java và Node
```bash
sudo yum update -y
sudo dnf install -y java-17-amazon-corretto
java -version
```