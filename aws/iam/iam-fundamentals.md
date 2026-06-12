# AWS IAM Fundamentals

## What is IAM?

IAM (Identity and Access Management) is the AWS service used to manage users, groups, permissions, and access to AWS resources.

---

## Root User vs IAM User

### Root User

- Full control of AWS account
- Created when AWS account is created
- Should not be used for daily work
- MFA should always be enabled

### IAM User

- Individual user account
- Permissions controlled through policies
- Used for daily administration

---

## IAM Components

### Users

Represent individual people or applications.

Example:

cloudadmin

### Groups

Collection of users.

Example:

s3Admins

### Policies

JSON documents that define permissions.

Examples:

AdministratorAccess
AmazonS3FullAccess

---

## Permission Flow

Policy
↓
Group
↓
User

Example:

AmazonS3FullAccess
↓
s3Admins
↓
cloudadmin

---

## AWS Managed Policies

Created and maintained by AWS.

Examples:

- AdministratorAccess
- AmazonS3FullAccess
- ReadOnlyAccess

---

## AdministratorAccess

Provides full access to AWS services and resources.

Suitable for learning environments but not recommended for normal enterprise users.

---

## Least Privilege Principle

Users should receive only the permissions necessary to perform their job responsibilities.

Benefits:

- Improved security
- Reduced risk of accidental changes
- Easier permission management

---

## Commands Used

aws sts get-caller-identity

aws iam list-users

aws iam list-groups

aws iam create-group --group-name s3Admins

aws iam attach-group-policy --group-name s3Admins --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess

aws iam add-user-to-group --user-name cloudadmin --group-name s3Admins

aws iam get-group --group-name s3Admins
