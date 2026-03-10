```markdown
# ⚡ Serverless REST API Using AWS Lambda + API Gateway

A beginner-friendly AWS project where you build a simple REST API using **AWS Lambda** and **Amazon API Gateway**.

This project demonstrates **serverless computing**, where AWS automatically manages the infrastructure so you can focus only on writing code.

---

# 📌 Project Overview

In this project, you will create a **REST API** that runs entirely on **serverless infrastructure**.

No servers, no EC2 instances, and no maintenance.

Your API will perform a simple function:

- Accept a **GET request**
- Trigger an **AWS Lambda function**
- Return a **JSON response**

This project is perfect for beginners learning **cloud backend development**.

---

# 🏗 Architecture Diagram

```

Client (Browser / Postman)
|
v
Amazon API Gateway
|
v
AWS Lambda Function
|
v
(Optional) Amazon DynamoDB

```

---

# 🧰 AWS Services Used

| Service | Purpose |
|------|------|
| **AWS Lambda** | Runs backend code without servers |
| **Amazon API Gateway** | Creates and manages REST APIs |
| **Amazon CloudWatch** | Logs and monitoring |
| **Amazon DynamoDB (Optional)** | Database for storing API data |

---

# 🎓 What You’ll Learn

By completing this project, you will learn:

- What **serverless architecture** is
- How to create **AWS Lambda functions**
- How to connect **API Gateway with Lambda**
- How to **deploy REST APIs**
- How to **test APIs using Postman / Browser / Curl**
- Basics of **event-driven architecture**

---

# 🧩 Sample Lambda Code

## Python Example

```python
import json

def lambda_handler(event, context):

    response = {
        "message": "Hello from AWS Lambda!",
        "input": event
    }

    return {
        "statusCode": 200,
        "body": json.dumps(response)
    }
````

---

# 🚀 Step-by-Step Deployment Guide

Follow the steps below to deploy the **Serverless REST API using AWS Lambda and API Gateway**.

---

# 1️⃣ Create a Lambda Function

1. Open **AWS Console**
2. Navigate to **Lambda**
3. Click **Create Function**
4. Choose **Author from scratch**

Configuration:

```
Function Name: hello-api
Runtime: Python 3.x
```

5. Click **Create Function**
6. Paste the **sample Lambda code**
7. Click **Deploy**

---

# 2️⃣ Create API Gateway

1. Go to **AWS Console → API Gateway**
2. Click **Create API**
3. Select **REST API**
4. Click **Build**

---

# 3️⃣ Create API Resource

Inside API Gateway:

Click **Create Resource**

Configuration:

```
Resource Name: hello
Resource Path: /hello
```

Click **Create Resource**

---

# 4️⃣ Create API Method

1. Select `/hello`
2. Click **Create Method**
3. Select **GET**

Integration settings:

```
Integration Type: Lambda Function
Lambda Function: hello-api
```

Click **Save**

---

# 5️⃣ Deploy the API

1. Click **Actions**
2. Select **Deploy API**

Create a new stage:

```
Stage Name: prod
```

Click **Deploy**

---

# 🔗 Invoke URL

After deployment, API Gateway will generate an **Invoke URL**.

Example:

```
https://abc123.execute-api.region.amazonaws.com/prod/hello
```

---

# 🧪 Test the API

## Browser

Paste the invoke URL:

```
https://abc123.execute-api.region.amazonaws.com/prod/hello
```

---

## Postman

Method:

```
GET
```

URL:

```
https://abc123.execute-api.region.amazonaws.com/prod/hello
```

---

## Curl

```bash
curl https://abc123.execute-api.region.amazonaws.com/prod/hello
```

---

# ✅ Expected Response

```json
{
  "message": "Hello from AWS Lambda!"
}
```

---

# 📊 CloudWatch Logs

To see logs from your Lambda function:

1. Go to **CloudWatch**
2. Click **Logs**
3. Open **Lambda log group**
4. View execution logs

---

# 🚀 Future Improvements

You can extend this project by adding:

* **POST API endpoint**
* **DynamoDB database**
* **Authentication using AWS Cognito**
* **Infrastructure as Code (Terraform / CloudFormation)**
* **CI/CD deployment pipeline**

---

# 🤝 Contributing

This repository is designed for **students and beginners learning AWS**.

Feel free to:

* ⭐ Star the repository
* 🐛 Report issues
* 🔧 Suggest improvements
* 📚 Add new cloud projects

---

# 📚 Learning Resources

* AWS Lambda Documentation
* AWS API Gateway Documentation
* Serverless Architecture Guide

---
