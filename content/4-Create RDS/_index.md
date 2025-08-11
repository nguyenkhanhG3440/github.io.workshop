---
title : "Create RDS"
date: 2025-06-18
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

# Create RDS PostgreSQL

1. RDS → **Create database**
2. Engine: **PostgreSQL**, Template: **Free tier**
3. DB instance identifier: `ctdemo-pg`
4. Master username: `postgres`, password: set strong
5. Instance class: `db.t3.micro`, Storage: GP3 (20GB)
6. **Connectivity**:
- Select EC2 VPC
- DB subnet group: default (or private subnet)
- Public access: **No**
- VPC SG: select SG for RDS, **open 5432 from EC2 SG**
7. Create database and wait for **Available**.

![Create RDS](/github.io.workshop/images/rds/001.png)
![Create RDS](/github.io.workshop/images/rds/002.png)
![Create RDS](/github.io.workshop/images/rds/003.png)
![Create RDS](/github.io.workshop/images/rds/004.png)
![Create RDS](/github.io.workshop/images/rds/005.png)
![Create RDS](/github.io.workshop/images/rds/006.png)

=> Select Clone if you do not want to use paid service
![Create RDS](/github.io.workshop/images/rds/007.png)
![Create RDS](/github.io.workshop/images/rds/008.png)
### Connect in EC2
```bash
sudo dnf install -y postgresql15
psql "host=<RDS-ENDPOINT> port=5432 user=postgres dbname=postgres password=<PASS>"