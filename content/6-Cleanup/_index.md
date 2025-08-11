+++
title = "Clean up resources"
date = 2022
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

We will take the following steps to delete the resources we created in this exercise.

### Step 1: Terminate EC2 Instances
Go to **AWS EC2 Console** → Select your instances → **Actions → Instance State → Terminate**.

### Step 2: Delete Security Groups and Key Pair
- Remove unused Security Groups.
- Delete the Key Pair to avoid reuse.

### Step 3: Delete RDS
- Go to **AWS RDS Console** → Select the created database.
- Click **Actions → Delete**.
- Uncheck **Create final snapshot** if you don’t need it.

### Step 4: Delete S3 Bucket
If you created an S3 bucket for logs, go to **AWS S3 Console** → Select the bucket → **Delete**.

### Step 5: Delete SES Identity and User
- Go to **AWS SES Console** → Select **Verified Identities** → Delete the verified email or domain.
- Go to **AWS IAM Console** → Delete the user/role created for SES.

### Step 6: Delete IAM Role (if not already deleted)
- Go to **AWS IAM Console** → Select the created role → **Delete**.
