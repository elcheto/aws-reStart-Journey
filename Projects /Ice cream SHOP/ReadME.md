## 🍦 Project Summary: Ice Cream Shop Digital Transformation

We are a team of five building a modern, cloud-based web solution for a local ice cream shop.

Our goal is to solve operational challenges—such as order mix-ups and high booking demand—by moving the business to the AWS cloud.

Using **AWS S3**, **CloudFront**, and **Cognito**, we are developing a secure and scalable static website that:
- Improves customer experience  
- Simplifies order management  
- Provides a professional online presence

  

# 🍦 Static Website: Ice Cream Shop (AWS S3)

## 1. Start Sandbox

1. Click **Start Lab** to launch the lab.
2. Wait until **"Lab status: ready"** appears.
3. Close the lab panel.

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
