<div align="center">

# 📸 SnapNotify

### Event-Driven Serverless Image Notification System

Automatically sends an email notification whenever an image is uploaded to Amazon S3 using AWS Lambda and Amazon SNS.

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazonaws)
![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python)
![Serverless](https://img.shields.io/badge/Architecture-Serverless-success)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)

</div>

---

## 📖 Overview

SnapNotify is a serverless AWS application that demonstrates **Event-Driven Architecture**.

Whenever a user uploads an image to Amazon S3, AWS automatically triggers a Lambda function, which publishes a notification to Amazon SNS. SNS then delivers an email notification to all subscribed recipients.

The project was built as part of the **CloudVerse** series to gain hands-on experience with core AWS services and serverless application development.

<p align="center">

![Demo](assets/demo.gif)

</p>

---

## 🏗️ Architecture

<p align="center">
  <img src="architecture/snapnotify-architecture.drawio.png" alt="SnapNotify Architecture" width="450">
</p>

---

## ⚙️ Workflow

```text
User Uploads Image
        │
        ▼
 Amazon S3 Bucket
        │
 Object Created Event
        ▼
 AWS Lambda Function
        │
   SNS Publish
        ▼
 Amazon SNS Topic
        │
        ▼
 Email Notification
```

---

## ☁️ AWS Services Used

| Service | Purpose |
|----------|---------|
| Amazon S3 | Object Storage |
| AWS Lambda | Event Processing |
| Amazon SNS | Email Notification |
| IAM | Access Control |
| CloudWatch | Logging & Monitoring |

---

## Features

- 📤 Upload images to Amazon S3
- ⚡ Automatic Lambda execution
- 📧 Instant email notifications
- ☁️ Fully serverless architecture
- 🔐 IAM least-privilege permissions
- 📊 CloudWatch logging

---

## 📂 Project Structure

```text
cloudverse-one-shot-01-snapnotify/

│
├── architecture/
│   ├── architecture.drawio
│   └── architecture.png
│
├── assets/
│   └── demo.gif
│
├── lambda/
│   └── lambda_function.py
│
├── screenshots/
│
├── docs/
│   ├── deployment-guide.md
│   ├── cleanup-guide.md
│   ├── faq.md
│   ├── troubleshooting.md
│   ├── cost-analysis.md
│   └── lessons-learned.md
│
├── README.md
├── LICENSE
└── .gitignore
```

---

## 📸 Screenshots

| AWS Console | Preview |
|-------------|---------|
| S3 Bucket | `screenshots/01-s3-bucket.png` |
| SNS Topic | `screenshots/02-sns-topic.png` |
| Email Subscription | `screenshots/03-email-subscription.png` |
| Lambda Function | `screenshots/04-lambda-function.png` |
| Environment Variables | `screenshots/05-environment-variable.png` |
| S3 Trigger | `screenshots/06-s3-trigger.png` |
| Email Notification | `screenshots/07-email-received.png` |
| CloudWatch Logs | `screenshots/08-cloudwatch-logs.png` |

---

## 🚀 Deployment

1. Create an Amazon S3 bucket.
2. Create an Amazon SNS topic and email subscription.
3. Create an AWS Lambda function.
4. Configure IAM permissions.
5. Add the SNS Topic ARN as an environment variable.
6. Configure the S3 trigger.
7. Upload an image and verify the email notification.

📄 Detailed deployment steps are available in:

```
docs/deployment-guide.md
```

---

## Documentation

Additional project documentation:

- 📖 Deployment Guide
- 🧹 Cleanup Guide
- ❓ FAQ
- 🛠️ Troubleshooting
- 💰 Cost Analysis
- 📘 Lessons Learned

All documentation is available inside the **docs/** folder.

---

## Future Enhancements

- Multiple email subscribers
- Amazon Recognition integration
- Image resizing
- Slack & Microsoft Teams notifications
- Metadata storage using DynamoDB
- API-based image upload

---

## 👩‍💻 Author

**Swanandi Helambe**

Aspiring Cloud Data Engineer

Building practical AWS projects through the **CloudVerse** series.

---

<div align="center">

⭐ If you found this project interesting, consider giving it a star!

</div>
