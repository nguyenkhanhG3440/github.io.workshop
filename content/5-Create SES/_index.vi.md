---
title : "Tạo Amazion SES"
date: 2025-06-18
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

## 1) Verify email identity
- SES → **Configuration → Identities → Create identity**
- Chọn **Email address**, nhập email của bạn → **Create**
- Vào hòm thư bấm **Verify**

## 2) Tạo SMTP user
- SES → **SMTP credentials → Create SMTP user**
- Tải **.csv** hoặc ghi lại **SMTP username** & **password**

Vào Configuration => Identities => create identity => nhập email => create
![SES SMTP](github.io.workshop/images/ses/001.png)
![SES SMTP](github.io.workshop/images/ses/002.png)
![SES SMTP](github.io.workshop/images/ses/003.png)
![SES SMTP](github.io.workshop/images/ses/004.png)

## 3) Cấu hình app (Spring Boot)
```properties
spring.mail.host=email-smtp.ap-southeast-1.amazonaws.com
spring.mail.port=587
spring.mail.username=<SMTP_USERNAME>
spring.mail.password=<SMTP_PASSWORD>
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true

app.mail.from=<email-đã-verify>