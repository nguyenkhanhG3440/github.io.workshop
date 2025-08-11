---
title : "Các bước tạo S3 + Lambda"
date: 2025-06-18
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

## 1 Tạo S3 bucket
1. Vào **S3 → Create bucket**.  
2. **Bucket name**: `your-unique-bucket-name` (phải **unique toàn cầu**).  
3. **AWS Region**: chọ​n cùng region với EC2/RDS (vd: `ap-southeast-1`).  
4. **Block Public Access**: **Giữ ON** (khuyến nghị).  
5. Create bucket.
6. Build lại dự án React => Upload file lênh S3

## 2. Tạo IAM Role cho Lambda

1. Vào **IAM → Roles → Create role**, chọn trusted entity là **Lambda**.  
2. Gắn quyền cho phép Lambda đọc/ghi vào bucket vừa tạo. Ví dụ **inline policy**:  

![Lambda](/images/s3Lambda/001.png)
![Lambda](/images/s3Lambda/002.png)


```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::your-unique-bucket-name/*"
    }
  ]
}
```

```bash
import json
import boto3
import base64
import os

s3 = boto3.client('s3')
BUCKET_NAME = os.environ.get("BUCKET_NAME", "your-unique-bucket-name")

def lambda_handler(event, context):
    file_data = base64.b64decode(event['pdfBase64'])
    file_key = f"certificates/{event['userId']}/{event['certificateId']}.pdf"

    s3.put_object(
        Bucket=BUCKET_NAME,
        Key=file_key,
        Body=file_data,
        ContentType="application/pdf"
    )

    return {
        "statusCode": 200,
        "body": json.dumps({
            "message": "File uploaded successfully",
            "fileKey": file_key
        })
    }
```

3. Cấu hình biến môi trường cho Lambda
```bash
BUCKET_NAME = your-unique-bucket-name
```

4. Test Lambda
## Đây event mẫu
```bash
{
  "userId": "user001",
  "certificateId": "cert-1001",
  "pdfBase64": "JVBERi0xLjQKJeLjz9MKNCAwIG9iago8PC9UeXBlIC9QYWdl..."
}
```

## Kết quả thực tế
```bash
{
  "statusCode": 200,
  "body": "{\"message\": \"File uploaded successfully\", \"fileKey\": \"certificates/u-001/cert-1001.pdf\"}"
}
```
- statusCode: 200 nghĩa là Lambda chạy thành công.
- message: Xác nhận file đã được upload lên S3.
- fileKey: Đường dẫn file trong bucket S3.

