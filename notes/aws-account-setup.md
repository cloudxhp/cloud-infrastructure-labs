# AWS Account Setup

## IAM

IAM stands for Identity and Access Management.

IAM is used to:
- create users
- manage permissions
- control access to AWS resources

IAM helps improve AWS account security by avoiding daily use of the root account.

---

## MFA

MFA stands for Multi-Factor Authentication.

MFA adds an additional security layer to AWS login by requiring:
- password
- authentication code from mobile device

Common MFA apps:
- Google Authenticator
- Microsoft Authenticator
- Authy

---

## Billing Alerts

Billing alerts help monitor AWS spending and prevent unexpected charges.

Purpose:
- cost control
- free tier monitoring
- usage notifications

Recommended beginner billing alert:
- $5 USD

---

## AWS CLI

AWS CLI (Command Line Interface) allows interaction with AWS services directly from the Linux terminal.

### Install AWS CLI

```bash
sudo apt install awscli
```

### Verify Installation

```bash
aws --version
```

### Configure AWS CLI

```bash
aws configure
```

Configuration requires:
- Access Key ID
- Secret Access Key
- Default region
- Output format

Recommended:
- Region = us-east-1
- Output = json

---

## Root Account vs IAM User

### Root Account
Primary AWS account with full unrestricted access.

Characteristics:
- complete account control
- highest security risk
- should not be used daily

---

### IAM User
User account with controlled permissions.

Characteristics:
- safer for daily usage
- permission-based access
- recommended for regular AWS work

Example:
- cloudadmin
