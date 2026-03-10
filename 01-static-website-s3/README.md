# 🌐 Static Website Hosting on Amazon S3

A beginner-friendly AWS project that teaches you how to host a static website using Amazon S3.  
This is one of the simplest and most popular cloud projects for students starting their cloud journey.

---

## 📌 Project Overview
In this project, you will deploy a static website (HTML/CSS/JS) to **Amazon S3** and configure it for public access.  
You’ll learn how cloud storage can be used to host websites without managing servers, making it a perfect first cloud project.

---

## 🏗 Architecture Diagram (ASCII)

User Browser
|
v
CloudFront (Optional)
|
v
Amazon S3 (Static Website Hosting)

---

## 🧰 AWS Services Used
- **Amazon S3** – Stores and serves your website files  
- **(Optional) Amazon CloudFront** – CDN for faster global delivery  
- **(Optional) Amazon Route 53** – Custom domain hosting  

---

## 🎓 What You’ll Learn
- How Amazon S3 stores and serves static files  
- Enabling static website hosting  
- Bucket policies & public access settings  
- Uploading and deploying website files  
- Basics of cloud security and permissions  

---

## 🚀 Step-by-Step Deployment Guide

### **1. Create an S3 Bucket**
- Go to **AWS Console → S3**
- Click **Create bucket**
- Bucket name must be **unique globally**
- Disable “Block all public access”
- Acknowledge the warning

### **2. Enable Static Website Hosting**
- Open your bucket → **Properties**
- Scroll to **Static website hosting**
- Enable it
- Set:
  - Index document: `index.html`
  - Error document: `error.html` (optional)

### **3. Upload Your Website Files**
## 🧪 Sample Website Included

This project includes a ready-to-deploy sample website inside the `src/` folder:

- `index.html`
- `styles.css`
- `script.js`
- `sample-image.png`

You can upload these files directly to your S3 bucket to instantly deploy your first cloud-hosted website.

Feel free to customize the content and redeploy to learn how S3 hosting works.

- Go to **Objects**
- Upload:
  - `index.html`
  - `styles.css`
  - `script.js`
  - images/assets

### **4. Set Public Read Permissions**
Create a bucket policy:

```json
{
    "Version": "2012-10-17",
    "Statement": [{
        "Sid": "PublicReadGetObject",
        "Effect": "Allow",
        "Principal": "*",
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }]
}
```


Replace `YOUR_BUCKET_NAME`.

### **5. Access Your Website**
Your website URL will look like:

http://YOUR_BUCKET_NAME.s3-website-REGION.amazonaws.com (your_bucket_name.s3-website-region.amazonaws.com in Bing)


---

## 🧪 Testing the Project
- Open the S3 website endpoint in your browser  
- Check if images, CSS, and JS load correctly  
- Test on mobile  
- Use DevTools → Network to confirm files load from S3  

---

## 💡 Optional Enhancements
- Add **CloudFront** for HTTPS + CDN  
- Add **Route 53** for a custom domain  
- Add **contact form** using API Gateway + Lambda  
- Add **versioning** to your S3 bucket  

---

## 🔗 GitHub Repository
All source code, architecture diagrams, and setup instructions are included in this folder.

