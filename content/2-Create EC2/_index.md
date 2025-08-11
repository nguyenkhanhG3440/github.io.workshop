---
title : "Create EC2 "
date: 2025-06-18
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

### Step 1: Launch instance
- AMI: **Amazon Linux 2023**
- Instance type: **t2.micro** (Free tier)
- Key pair: create/download `.pem` file
- Security Group: open **22/TCP** (restrict your IP)
- Launch

![Launch EC2](/github.io.workshopimages/ec2/001.png)


### Create key pair

![Launch EC2](/github.io.workshop/images/ec2/002.png)

### Network setting

![Launch EC2](/github.io.workshop/images/ec2/003.png)
![Launch EC2](/github.io.workshop/images/ec2/004.png)
![Launch EC2](/github.io.workshop/images/ec2/005.png)

### Bước 2: SSH vào EC2

![Launch EC2](/github.io.workshop/images/ec2/006.png)
```bash
chmod 400 your-key.pem
ssh -i your-key.pem ec2-user@<EC2-Public-IP>
```

### Bước 3 : Install Java and Node
```bash
sudo yum update -y
sudo dnf install -y java-17-amazon-corretto
java -version
```

