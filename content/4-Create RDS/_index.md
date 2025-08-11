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

{{< figure src="images/rds/001.png" alt="Create RDS" >}}

{{< figure src="images/rds/002.png" alt="Create RDS" >}}

{{< figure src="images/rds/003.png" alt="Create RDS" >}}

{{< figure src="images/rds/004.png" alt="Create RDS" >}}

{{< figure src="images/rds/005.png" alt="Create RDS" >}}

{{< figure src="images/rds/006.png" alt="Create RDS" >}}



=> Select Clone if you do not want to use paid service
{{< figure src="images/rds/007.png" alt="Create RDS" >}}

{{< figure src="images/rds/008.png" alt="Create RDS" >}}
### Connect in EC2
```bash
sudo dnf install -y postgresql15
psql "host=<RDS-ENDPOINT> port=5432 user=postgres dbname=postgres password=<PASS>"