# 📘 SnapNotify Deployment Guide

This guide provides step-by-step instructions to deploy the **SnapNotify** project on AWS. By following this guide, you will create a fully serverless application that automatically sends an email notification whenever an image is uploaded to an Amazon S3 bucket.

---

## 🎯 Objective

Deploy an event-driven serverless application using Amazon S3, AWS Lambda, and Amazon SNS to automatically notify users when a new image is uploaded.

---

## 🏗️ Architecture

<p align="center">
    <img src="architecture/snapnotify-architecture.drawio.png" alt="SnapNotify Architecture" width="500">
</p>

---

## 📋 Prerequisites

Before starting, ensure you have:

- An AWS Account
- Access to the AWS Management Console
- A verified email address for Amazon SNS notifications
- Basic knowledge of AWS services (S3, Lambda, SNS)

---

> **Important**
>
> All screenshots in this guide are numbered in the order of execution to simplify navigation.
>
> Configure **only** the options explicitly mentioned in each step or highlighted in the screenshots.
>
> Unless otherwise specified, leave all other AWS settings at their **default values**.

---

# Step 1 – Create an Amazon S3 Bucket

## Objective

Create an Amazon S3 bucket that stores uploaded images and generates an event whenever a new object is created.

## Procedure

1. Sign in to the AWS Management Console.
2. Search for **Amazon S3**.
3. Click **Create bucket**.
4. Enter a globally unique bucket name.
5. Select your preferred AWS Region.
6. Keep all remaining settings as their default values.
7. Click **Create bucket**.

## Screenshots

*(Insert screenshots here)*

## Verification

Verify that:

- The bucket appears in the S3 Console.
- The bucket contains no objects.
- Bucket status is successfully created.

---

# Step 2 – Create an Amazon SNS Topic

## Objective

Create an SNS topic that will send email notifications whenever a new image is uploaded.

## Procedure

1. Open **Amazon SNS**.
2. Navigate to **Topics**.
3. Click **Create topic**.
4. Select **Standard**.
5. Enter the topic name.
6. Leave all remaining settings at their default values.
7. Click **Create topic**.

## Screenshots

*(Insert screenshots here)*

## Verification

Verify that the SNS topic appears in the Topics list.

---

# Step 3 – Create an Email Subscription

## Objective

Subscribe an email address to receive notifications from the SNS topic.

## Procedure

1. Open the SNS topic.
2. Click **Create subscription**.
3. Select **Email** as the protocol.
4. Enter your email address.
5. Click **Create subscription**.
6. Open your inbox.
7. Confirm the subscription.

## Screenshots

*(Insert screenshots here)*

## Verification

Ensure the subscription status changes from **Pending Confirmation** to **Confirmed**.

---

# Step 4 – Create the AWS Lambda Function

*(We'll write this after completing Steps 1–3.)*

---

# Step 5 – Configure IAM Permissions

*(To be added.)*

---

# Step 6 – Configure Environment Variables

*(To be added.)*

---

# Step 7 – Configure the S3 Trigger

*(To be added.)*

---

# Step 8 – Test the Project

*(To be added.)*

---

# ✅ Expected Output

After uploading an image to Amazon S3:

- AWS Lambda should execute automatically.
- Amazon SNS should publish a notification.
- A notification email should be delivered to the subscribed email address.

---

# 📚 Additional Resources

For more details, refer to:

- `faq.md`
- `troubleshooting.md`
- `cleanup-guide.md`
