This lab demonstrates how to use the AWS CLI to create an S3 bucket, manage IAM permissions, and deploy a static website using a repeatable script.

## 📋 Lab Overview
Duration: ~45 minutes

Key Services: Amazon S3, IAM, Amazon EC2, AWS Systems Manager (SSM).

Goal: Deploy a Café & Bakery website to S3 and automate updates via a Bash script.

## 🚀 Getting Started
Start Lab: Click Start Lab and wait for the "Ready" status.

Open Console: Click the AWS button to open the Management Console in a new tab.

Note: Do not change the AWS Region unless instructed.

### 🛠️ Task 1: Connect to EC2 via SSM
In the lab interface, select Details > Show.

Copy the InstanceSessionUrl and open it in a new tab.

In the terminal, switch to the ec2-user:

Bash
sudo su -l ec2-user
pwd

<img width="500" height="300" alt="Task 1" src="https://github.com/user-attachments/assets/87673e0a-f9b5-445a-ad10-4a7a0b489f8f" />

### ⚙️ Task 2: Configure AWS CLI
Initialize the CLI with your lab credentials:

Run aws configure.

Access Key / Secret Key: Copy from the lab "Details" panel.

Default region: us-west-2

Output format: json

<img width="500" height="100" alt="Task 2" src="https://github.com/user-attachments/assets/05abbd17-8c95-4144-8023-d5529f14e266" />


### 📦 Task 3: Create the S3 Bucket
Bucket names must be globally unique. Use a pattern like initial-lastname-123.

Bash
# Replace <your-bucket-name> with a unique name
aws s3api create-bucket --bucket <your-bucket-name> --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2
👤 Task 4: IAM & Permissions
Create User: ```bash
aws iam create-user --user-name awsS3user
aws iam create-login-profile --user-name awsS3user --password Training123!

Attach Policy: Find the S3 Full Access policy and attach it.

Bash
# Search for the policy ARN
aws iam list-policies --query "Policies[?contains(PolicyName,'S3FullAccess')].Arn"

# Attach it (replace <PolicyArn> with the result from above)
aws iam attach-user-policy --user-name awsS3user --policy-arn <PolicyArn>

### 🔓 Task 5: Adjust S3 Public Access
To host a website, the bucket must allow public reads:

In the S3 Console, select your bucket.

Permissions Tab: * Disable Block all public access.

Edit Object Ownership and enable ACLs.

### 🌐 Task 6 & 7: Deploy the Website
Extract Files:

Bash
cd ~/sysops-activity-files
tar xvzf static-website-v2.tar.gz
cd static-website
Enable Hosting:

Bash
aws s3 website s3://<your-bucket-name>/ --index-document index.html
Upload Content:

Bash
aws s3 cp . s3://<your-bucket-name>/ --recursive --acl public-read
View Site: Find the Bucket website endpoint at the bottom of the Properties tab in the S3 console.

### 📜 Task 8: Automate with a Script
Create a script to push local changes to S3 automatically.

Create Script: vi ~/update-website.sh

Add Content:

Bash
#!/bin/bash
aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<your-bucket-name>/ --recursive --acl public-read
Execute:

Bash
chmod +x ~/update-website.sh
./update-website.sh
💡 Optional Challenge: Efficiency
Replace cp with sync in your script to only upload modified files:

Bash
aws s3 sync /home/ec2-user/sysops-activity-files/static-website/ s3://<your-bucket-name>/ --acl public-read
