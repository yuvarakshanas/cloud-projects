# 🔄 CI/CD Pipeline Using AWS CodePipeline

A beginner‑friendly DevOps project where you build a fully automated CI/CD pipeline using **AWS CodePipeline**, **AWS CodeBuild**, and **Amazon S3 or Elastic Beanstalk**.  
This project teaches automation, continuous deployment, and how modern cloud applications are delivered in real‑world environments.

---

## 📌 Project Overview

In this project, you will create a CI/CD pipeline that automatically deploys code from GitHub to AWS.  
Whenever you push new code:

1. **CodePipeline** detects the change  
2. **CodeBuild** builds and tests the application  
3. The application is deployed to **S3** (static site) or **Elastic Beanstalk** (web app)

This project is perfect for beginners learning DevOps and cloud automation.

---

## 🏗 Architecture Diagram (ASCII)

```
GitHub Repository
        |
        v
   AWS CodePipeline
        |
        v
   AWS CodeBuild  ----> (Optional: Tests)
        |
        v
S3 Bucket (Static Website)  OR  Elastic Beanstalk (Web App)
```

---

## 🧰 AWS Services Used

- **AWS CodePipeline** – Automates the CI/CD workflow  
- **AWS CodeBuild** – Builds and tests your code  
- **Amazon S3** – Deploy static websites  
- **Elastic Beanstalk** – Deploy backend applications  
- **IAM** – Permissions for pipeline and build roles  

---

## 🎓 What You’ll Learn

- How CI/CD pipelines work  
- Automating deployments  
- Connecting GitHub to AWS  
- Creating and using `buildspec.yml`  
- Deploying to S3 or Elastic Beanstalk  
- Understanding DevOps workflows  

---

# 🧩 Sample Buildspec Files

## Static Website Deployment to S3**

```yaml
version: 0.2

phases:
  install:
    commands:
      - echo "Installing dependencies..."
  build:
    commands:
      - echo "Building static website..."
  post_build:
    commands:
      - aws s3 sync . s3://YOUR_BUCKET_NAME --delete

artifacts:
  files:
    - '**/*'
```

---

# 🚀 Step‑by‑Step Deployment Guide

## **1. Create a GitHub Repository**
- Add your sample app files  
- Add `buildspec.yml`  
- Push to GitHub  

---

## **2. Create Deployment Target**

### S3 (Static Website)**
- Create an S3 bucket  
- Enable static website hosting  

---

## **3. Create a CodeBuild Project**
- Select your GitHub repo  
- Choose runtime (Node.js, Python, etc.)  
- Ensure `buildspec.yml` is in the root folder  

---

## **4. Create a CodePipeline**
- Go to **AWS CodePipeline**  
- Click **Create pipeline**  
- Source: GitHub  
- Build: CodeBuild  
- Deploy: S3 or Elastic Beanstalk  

---

## **5. Push Code to Trigger Deployment**

```
git add .
git commit -m "Initial commit"
git push
```

Pipeline will automatically:

1. Detect the change  
2. Build the project  
3. Deploy it  

---

# 🧪 Testing the Pipeline

### **For S3 Deployment**
Visit:

```
http://YOUR_BUCKET_NAME.s3-website-REGION.amazonaws.com
```

### **For Elastic Beanstalk**
Visit:

```
http://your-env.elasticbeanstalk.com
```

### **Check Logs**
- CodeBuild logs  
- CodePipeline execution history  

---

# 💡 Optional Enhancements

- Add automated tests  
- Add CloudFront for CDN  
- Add SNS notifications  
- Add manual approval steps  
- Add multi‑stage pipelines (dev → test → prod)  

---