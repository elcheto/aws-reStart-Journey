## 🍦🍦🍦 Static Website: Ice Cream Shop (AWS S3) 🍦🍦🍦
<img width="600" height="350" alt="Screenshot 2026-03-19 at 13 51 35" src="https://github.com/user-attachments/assets/95315ecd-1735-430c-80ee-e68720097dc4" />


We are a team of five building a modern, cloud-based web solution for a local ice cream shop.

Our goal is to solve operational challenges—such as order mix-ups and high booking demand—by moving the business to the AWS cloud.

Using **AWS S3**, **CloudFront**, and **Cognito**, we are developing a secure and scalable static website that:
- Improves customer experience  
- Simplifies order management  
- Provides a professional online presence


## 1. Start Sandbox

1. Click **Start Lab** to launch the lab.
2. Wait until **"Lab status: ready"** appears.
3. Close the lab panel.

4. <img width="600" height="350" alt="image (2)" src="https://github.com/user-attachments/assets/b9b63ee4-3ce2-4734-8671-1077d521a84a" />


## 2. Access AWS Management Console

1. Click **AWS** (top-left corner).
2. The AWS Management Console will open in a new tab and sign you in automatically.
3. If the tab doesn’t open:
   - Enable pop-ups in your browser
   - Try again
4. Arrange the AWS Console and these instructions side by side for easier setup.


## 3. Create an S3 Bucket

1. Open the S3 console: https://console.aws.amazon.com/s3/
2. Click **Create bucket**.
3. Enter a bucket name: `static-website-icecream-shop`.
4. Select a **Region**:
   - Choose one close to you for lower latency and cost
   - The region determines your website endpoint
5. Under **Block Public Access settings**:
   - Uncheck **Block all public access**
   - Check the acknowledgment box
6. Leave the remaining settings as default.
7. Click **Create bucket**.

## 4. Enable Static Website Hosting

1. Open the S3 console: https://console.aws.amazon.com/s3/
2. Click **General purpose buckets**.
3. Select your bucket.
4. Go to the **Properties** tab.
5. Scroll to **Static website hosting** and click **Edit**.
6. Select **Use this bucket to host a website**.
7. Enable static website hosting.
8. Enter `index.html` as the **Index document** (case-sensitive).
9. Click **Save changes**.
10. Copy the **Website endpoint URL** to test your site.


## 5. Add Bucket Policy (Public Access)

1. Open the S3 console: https://console.aws.amazon.com/s3/
2. Select your bucket: `static-website-icecream-shop`.
3. Go to the **Permissions** tab.
4. Scroll to **Bucket policy** and click **Edit**.
5. Paste the policy below into the editor.
6. Ensure the bucket name is `static-website-icecream-shop`.
7. Click **Save changes**.

### Bucket Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::static-website-icecream-shop/*"]
    }
  ]
}
