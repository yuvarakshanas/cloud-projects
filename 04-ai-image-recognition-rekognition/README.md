# ✅ **`04-ai-image-recognition-rekognition/README.md` (Copy & Paste)**

```md
# 🤖 AI Image Recognition App Using AWS Rekognition

A beginner-friendly AWS project where you build an image recognition system using **Amazon Rekognition**.  
Users upload an image to S3, and a Lambda function automatically analyzes it using Rekognition and returns detected labels, objects, and confidence scores.

This project introduces cloud-based AI, event-driven architecture, and serverless workflows.

---

## 📌 Project Overview
In this project, you will:

1. Upload an image to an S3 bucket  
2. Trigger a Lambda function automatically  
3. Analyze the image using Amazon Rekognition  
4. Return labels such as:  
   - Person  
   - Car  
   - Animal  
   - Text  
   - Objects  

This is a perfect introduction to AI/ML services on AWS.

---

## 🏗 Architecture Diagram (ASCII)

```
User Uploads Image
        |
        v
Amazon S3 (Image Bucket)
        |
   S3 Event Trigger
        |
        v
AWS Lambda (Process Image)
        |
        v
Amazon Rekognition (Detect Labels)
        |
        v
CloudWatch Logs / API Response
```

---

## 🧰 AWS Services Used
- **Amazon S3** – Stores uploaded images  
- **AWS Lambda** – Processes the image  
- **Amazon Rekognition** – Detects labels and objects  
- **Amazon CloudWatch** – Logs and monitoring  

---

## 🎓 What You’ll Learn
- How AI services work on AWS  
- Image recognition basics  
- Event-driven architecture  
- Integrating S3 → Lambda → Rekognition  
- Parsing JSON responses  
- Logging and debugging with CloudWatch  

---

# 🧩 Sample Lambda Code (Included in Repo)

## **Option 1: Node.js (index.js)**

```javascript
const AWS = require("aws-sdk");
const rekognition = new AWS.Rekognition();

exports.handler = async (event) => {
    const bucket = event.Records[0].s3.bucket.name;
    const key = event.Records[0].s3.object.key;

    const params = {
        Image: {
            S3Object: {
                Bucket: bucket,
                Name: key
            }
        },
        MaxLabels: 10,
        MinConfidence: 70
    };

    const result = await rekognition.detectLabels(params).promise();

    console.log("Detected Labels:", JSON.stringify(result.Labels, null, 2));

    return {
        statusCode: 200,
        body: JSON.stringify(result.Labels)
    };
};
```

---

## **Option 2: Python (index.py)**

```python
import json
import boto3

rekognition = boto3.client('rekognition')

def lambda_handler(event, context):
    bucket = event["Records"][0]["s3"]["bucket"]["name"]
    key = event["Records"][0]["s3"]["object"]["key"]

    response = rekognition.detect_labels(
        Image={
            "S3Object": {
                "Bucket": bucket,
                "Name": key
            }
        },
        MaxLabels=10,
        MinConfidence=70
    )

    print("Detected Labels:", json.dumps(response["Labels"], indent=2))

    return {
        "statusCode": 200,
        "body": json.dumps(response["Labels"])
    }
```

---

# 🚀 Step-by-Step Deployment Guide

## **1. Create an S3 Bucket**
- Go to **AWS Console → S3**
- Create a bucket (e.g., `rekognition-image-bucket`)
- Enable default settings

---

## **2. Create a Lambda Function**
- Go to **AWS Lambda**
- Create a new function  
- Runtime: Node.js or Python  
- Paste the sample code  
- Add permissions for Rekognition + S3  

IAM policy required:

```
rekognition:DetectLabels
s3:GetObject
```

---

## **3. Add S3 Trigger**
- Open your Lambda function  
- Add trigger → **S3**  
- Event type: **PUT**  
- This means: *Whenever an image is uploaded, Lambda runs automatically*

---

## **4. Upload an Image**
Upload any image to your S3 bucket:

- dog  
- car  
- person  
- animal  
- object  

Lambda will run automatically.

---

## **5. Check Results**
Go to:

**CloudWatch → Logs → Your Lambda Function**

You will see output like:

```json
[
  { "Name": "Dog", "Confidence": 98.5 },
  { "Name": "Animal", "Confidence": 97.2 },
  { "Name": "Pet", "Confidence": 95.1 }
]
```

---

# 🧪 Testing Checklist
- Upload image → Lambda triggers  
- Rekognition returns labels  
- Logs appear in CloudWatch  
- Confidence scores are correct  
- Errors handled gracefully  

---

# 💡 Optional Enhancements
- Add API Gateway to return results to a frontend  
- Store results in DynamoDB  
- Build a React UI to display labels  
- Add Rekognition **Text Detection**  
- Add Rekognition **Face Detection**  

---
