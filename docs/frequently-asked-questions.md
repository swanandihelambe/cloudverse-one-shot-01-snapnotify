# SnapNotify FAQ

## Overview

This document answers common questions about the SnapNotify project, including its architecture, design decisions, AWS services used, and potential enhancements. It serves as both a project reference and an interview preparation resource.

---

# General Questions

## What is SnapNotify?

SnapNotify is a serverless, event-driven AWS application that automatically sends an email notification whenever an image is uploaded to an Amazon S3 bucket.

---

## What problem does SnapNotify solve?

The project demonstrates how AWS services can automatically respond to events without requiring manual intervention. Instead of continuously checking for new uploads, the system reacts immediately when an object is created in Amazon S3.

---

## Which AWS services are used?

- Amazon S3
- AWS Lambda
- Amazon SNS
- AWS IAM
- Amazon CloudWatch

---

# Architecture & Design Decisions

## Why was Amazon S3 used?

Amazon S3 provides highly durable and scalable object storage. It also supports native event notifications, making it an ideal choice for triggering serverless workflows.

---

## Why was AWS Lambda used instead of Amazon EC2?

AWS Lambda was selected because the application only needs to execute code in response to an event. Unlike Amazon EC2, Lambda requires no server management, scales automatically, and follows a pay-per-use pricing model.

---

## Why was Amazon SNS used instead of Amazon SES?

Amazon SNS was chosen because the project only needs to publish notifications to subscribed recipients.

Amazon SES is designed for sending transactional or bulk emails, whereas Amazon SNS provides a simple publish-subscribe messaging model that is better suited for event notifications.

---

## Why is an IAM execution role required?

AWS Lambda requires permission to interact with other AWS services.

The IAM execution role grants the Lambda function permission to:

- Write logs to Amazon CloudWatch
- Publish notifications to Amazon SNS

without exposing unnecessary permissions.

---

## Why is the SNS Topic ARN stored as an environment variable?

Using environment variables separates configuration from application code.

This approach improves maintainability, avoids hardcoding resource identifiers, and makes it easier to deploy the same code across different AWS environments.

---

# Event-Driven Architecture

## What is Event-Driven Architecture?

Event-Driven Architecture is a design pattern where system components respond automatically to events.

In SnapNotify, uploading an image to Amazon S3 generates an **Object Created** event, which triggers the AWS Lambda function.

---

## What happens when an image is uploaded?

1. The image is uploaded to Amazon S3.
2. Amazon S3 generates an Object Created event.
3. AWS Lambda is invoked automatically.
4. Lambda publishes a message to Amazon SNS.
5. Amazon SNS sends an email notification to the subscribed recipient.

---

## How are notifications delivered?

AWS Lambda publishes a message to an Amazon SNS topic.

Amazon SNS then forwards the notification to all confirmed email subscribers associated with that topic.

---

# Security

## How is the project secured?

The project follows the principle of least privilege by granting the Lambda execution role only the permissions required to publish notifications and write logs.

Additionally:

- The SNS Topic ARN is stored as an environment variable.
- AWS-managed IAM policies are used where appropriate.
- Amazon CloudWatch records all Lambda executions for monitoring and debugging.

---

# Future Enhancements

## How can this project be extended?

Possible enhancements include:

- SMS notifications using Amazon SNS
- Slack or Microsoft Teams notifications
- Metadata storage using Amazon DynamoDB
- Automatic image resizing
- Amazon Rekognition integration for image analysis
- REST API using Amazon API Gateway

---

# Interview Questions

## What AWS concepts does this project demonstrate?

- Serverless Computing
- Event-Driven Architecture
- Object Storage
- Publish-Subscribe Messaging
- IAM Permission Management
- Cloud Monitoring using Amazon CloudWatch

---

## Which AWS services trigger one another?

Amazon S3 → AWS Lambda → Amazon SNS

This sequence forms the core event-driven workflow of the project.

---

## What were the key learning outcomes?

This project provided practical experience with:

- Configuring Amazon S3 event notifications
- Developing AWS Lambda functions
- Publishing notifications using Amazon SNS
- Managing IAM permissions
- Monitoring Lambda execution with Amazon CloudWatch
- Designing a basic event-driven serverless application

---

## Additional Resources

For deployment instructions, refer to:

- deployment-guide.md

For common deployment issues, refer to:

- troubleshooting-guide.md

For resource cleanup, refer to:

- cleanup-guide.md
