# SnapNotify Troubleshooting Guide

## Overview

This document lists common issues that may be encountered while deploying or testing the SnapNotify project, along with their possible causes and recommended solutions.

---

# Issue 1 – Lambda Function Is Not Triggered

## Symptoms

- Uploading an image to Amazon S3 does not invoke the Lambda function.
- No new Lambda invocations appear in Amazon CloudWatch.

## Possible Causes

- Amazon S3 trigger has not been configured.
- Incorrect S3 bucket selected while creating the trigger.
- Trigger is disabled.

## Resolution

1. Open the AWS Lambda Console.
2. Select the **snapnotify-lambda** function.
3. Verify that the Amazon S3 trigger exists.
4. Ensure the correct S3 bucket is selected.
5. Confirm that the trigger is enabled.

---

# Issue 2 – Email Notification Is Not Received

## Symptoms

- Image upload is successful.
- Lambda executes successfully.
- No email notification is received.

## Possible Causes

- Amazon SNS subscription has not been confirmed.
- Incorrect email address.
- Email is located in the Spam or Junk folder.

## Resolution

1. Open the Amazon SNS Console.
2. Navigate to **Subscriptions**.
3. Verify that the subscription status is **Confirmed**.
4. Check the Spam or Junk folder.
5. Upload another image and test again.

---

# Issue 3 – AccessDeniedException While Publishing to Amazon SNS

## Symptoms

CloudWatch displays an error similar to:

```
AccessDeniedException
```

## Possible Cause

The Lambda execution role does not have permission to publish messages to Amazon SNS.

## Resolution

1. Open the Lambda execution role.
2. Create an inline IAM policy.
3. Grant the `sns:Publish` permission.
4. Save the policy and test again.

---

# Issue 4 – Environment Variable Not Found

## Symptoms

Lambda execution fails with an error similar to:

```
KeyError: SNS_TOPIC_ARN
```

## Possible Cause

The `SNS_TOPIC_ARN` environment variable has not been configured or contains an incorrect value.

## Resolution

1. Open the Lambda function.
2. Navigate to **Configuration → Environment Variables**.
3. Verify that:

| Key | Value |
|-----|------|
| SNS_TOPIC_ARN | Valid SNS Topic ARN |

4. Save the changes and deploy the function again.

---

# Issue 5 – Unable to Delete the Amazon S3 Bucket

## Symptoms

Amazon S3 displays:

```
Bucket is not empty.
```

## Possible Cause

Objects still exist inside the bucket.

## Resolution

1. Open the S3 bucket.
2. Delete all objects.
3. Return to the bucket list.
4. Delete the bucket.

---

# Issue 6 – Lambda Code Changes Are Not Reflected

## Symptoms

The Lambda function continues using the old version of the code.

## Possible Cause

The updated code was not deployed.

## Resolution

1. Open the Lambda Code editor.
2. Click **Deploy**.
3. Wait for the confirmation message.
4. Test the application again.

---

# Issue 7 – Image Upload Does Not Generate an Event

## Symptoms

Uploading an image to Amazon S3 completes successfully, but Lambda is never invoked.

## Possible Causes

- Incorrect event type selected.
- Event notification not configured.
- Upload performed to a different bucket.

## Resolution

Verify that the trigger is configured for:

- Event Type: **All Object Create Events**
- Correct Amazon S3 bucket
- Trigger Status: **Enabled**

---

# Debugging Tips

When troubleshooting SnapNotify, verify resources in the following order:

1. Amazon S3
2. AWS Lambda Trigger
3. Lambda Execution Logs (Amazon CloudWatch)
4. IAM Permissions
5. Amazon SNS Topic
6. Amazon SNS Subscription

Following this sequence helps isolate the root cause more efficiently.

---

# Additional Resources

For deployment instructions, refer to:

- `deployment-guide.md`

For project-specific questions, refer to:

- `faq.md`
