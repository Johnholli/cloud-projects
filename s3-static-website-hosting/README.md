# 🖥️ AWS S3 Static Website Hosting

![Built with AWS](https://img.shields.io/badge/Built%20with-AWS-orange?logo=amazon-aws&logoColor=white)
![Static Website](https://img.shields.io/badge/Hosted%20on-S3-blue?logo=amazon-s3)
![HTML/CSS](https://img.shields.io/badge/Code-HTML%20%7C%20CSS-green?logo=html5&logoColor=white)

This project demonstrates how to host a static website using **Amazon S3**, including:
- Creating and configuring an S3 bucket
- Simulating folder structures (`images/`, `css/`)
- Uploading content via AWS Console
- Applying a custom bucket policy to control public access to specific folders

---

## 📁 Folder Structure

```
s3-static-website-hosting/
├── index.html
├── images/
│   └── logo.png
├── css/
│   └── style.css
├── screenshots/
│   └── (images shown below)
├── bucket-policy.json
└── README.md
```

---

## 🚀 Steps to Deploy

### 1. Create the S3 Bucket
- Use the AWS Console
- Uncheck "Block all public access"
- Enable **Static Website Hosting** in the bucket settings

### 2. Upload Files
- Use the **“Create Folder”** feature to simulate folders
- Upload `index.html` to root
- Upload files into `/images/` and `/css/`

### 3. Apply a Bucket Policy (Only `/images` Public)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicReadOnlyImages",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::s3-static-website-1-420/images/*"
    }
  ]
}
```

### 4. Test Public Access
- Open the object URL of a file in `/images/` → should load
- Try accessing a file in `/css/` → should return **Access Denied**

---

## 🌐 Result

- ✅ Public: `https://s3-static-website-1-420.s3.us-east-1.amazonaws.com/images/Montauk+i-495+Logo.png`
- ❌ Private: `/css/style.css` or `index.html`

---

## 🛠️ Technologies Used
- Amazon S3
- AWS Management Console
- HTML/CSS

---

## 📚 What I Learned
- How to simulate directory structures in S3
- How to restrict access using prefix-based bucket policies
- How to host and test a live static website on S3

---

## 📸 Screenshots

### 🔹 S3 Bucket Configuration
<img src="screenshots/s3-bucket-settings.png" alt="S3 Bucket Static Website Settings" width="600"/>

### 🔹 Public File Access
<img src="screenshots/public-file-access.png" alt="Public Access to /images/logo.png" width="600"/>

### 🔹 Access Denied for Private File
<img src="screenshots/private-file-denied.png" alt="Access Denied for /css/style.css" width="600"/>

---
