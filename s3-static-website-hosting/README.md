# 🖥️ AWS S3 Static Website Hosting 

![Built with AWS](https://img.shields.io/badge/Built%20with-AWS-orange?logo=amazon-aws&logoColor=white)
![Static Website](https://img.shields.io/badge/Hosted%20on-S3-blue?logo=amazon-s3)
![HTML/CSS](https://img.shields.io/badge/Code-HTML%20%7C%20CSS-green?logo=html5&logoColor=white)

![Aws-S3--Streamline-Svg-Logos-2](https://github.com/user-attachments/assets/52cf05e5-aceb-47d6-8895-58e0cc58a294)

This project demonstrates how to host a static website using **Amazon S3**, including:
- Creating and configuring an S3 bucket
- Uploading and organizing site files
- Hosting custom HTML/CSS content
- Applying a custom bucket policy to control public access
- Setting up S3 for static website hosting
- (Optional) Configuring CloudFront for HTTPS
- (Optional) Connecting a domain using Route 53

---

## 🖼️ Architecture Diagram

This diagram illustrates the AWS services and workflow used to deploy this project:

![AWS Hosting Architecture](images/aws-architecture.png)

---

## 🛠️ Tech Stack

- Amazon Web Services:
  - S3 (Website Hosting)
  - IAM (Access Policies)
  - AWS Management Console
  - AWS CLI 
  - CloudFront (CDN + HTTPS, optional)
  - Route 53 (Custom Domain, optional)
- HTML / CSS

## 📁 Folder Structure

```
s3-static-website-hosting/
├── README.md
├── bucket-policy.json
├── index.html
└── error.html
```

---

## 🚀 How to Deploy

### 1. Create the S3 Bucket
- Open the AWS Console
- Click **Create Bucket**
- Name it and uncheck **Block all public access**
- Enable **Static Website Hosting**

### 2. Upload Your Files
- Upload your website files: `index.html`, `error.html`, `/css`, `/images`
- Use **Create Folder** in S3 to simulate folder structure

### 3. Apply a Bucket Policy

To make only the `/images/` folder public:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicReadOnlyImages",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::jholly-bucket-4-24-25/images/*"
    }
  ]
}
```

### 4. Test Public Access
- Open the object URL of a file in `/images/` → should load
- Try accessing a file in `/css/` → should return **Access Denied**

---

## 🌐 Result

- ✅ Public: `http://jholly-bucket-4-24-25.s3-website-us-east-1.amazonaws.com`
- ❌ Private: `/css/style.css` or `index.html`

---

## 📚 What I Learned

- How to simulate directories in S3 using folder prefixes
- How to write IAM bucket policies for granular access
- How to use AWS services like CloudFront and Route 53 with static sites
- How to host and test real-world cloud-based content

---

## 📸 Screenshots

### 🔹 S3 Bucket Configuration
<img width="1083" alt="s3-bucket-settings" src="https://github.com/user-attachments/assets/1bf674a4-9f5c-402c-a610-3cc9f2b3da67" />

### 🔹 Public File Access
<img src="screenshots/public-file-access.png" alt="Public Access to /images/logo.png" width="600"/>

### 🔹 Access Denied for Private File
<img src="screenshots/private-file-denied.png" alt="Access Denied for /css/style.css" width="600"/>

---
