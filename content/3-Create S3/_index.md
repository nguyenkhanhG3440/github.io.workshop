---
title : "Create S3 and Lambda"
date: 2025-06-18
weight : 3
chapter : false
pre : " <b> 3. </b> "
---


## 1) Create S3 Bucket

### Method 1 — AWS Console
1. Go to **S3 → Create Bucket**.

2. **Bucket Name**: `your unique bucket-name` (must be **globally unique**).
3. **AWS Region**: select the same region as EC2/RDS (e.g. `ap-southeast-1`).
4. **Prohibit Public Access**: **Keep ON** (recommended).
5. Create Bucket.


![Lambda](/github.io.workshop/images/s3Lambda/001.png)
![Lambda](/github.io.workshop/images/s3Lambda/002.png)


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

- statusCode: 200 means Lambda ran successfully.
- message: Confirmed file uploaded to S3.
- fileKey: File path in S3 bucket.