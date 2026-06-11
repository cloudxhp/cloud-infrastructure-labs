# AWS S3 Fundamentals

## Objective

Learn how to create Amazon S3 buckets and manage objects using the AWS Command Line Interface (CLI).

This lab introduced the core concepts of AWS object storage and demonstrated common operations used by Cloud Engineers, Cloud Support Engineers, and DevOps Engineers.

---

# What is Amazon S3?

Amazon S3 (Simple Storage Service) is AWS's object storage service.

S3 is designed to provide:

* High durability
* High availability
* Scalability
* Secure data storage
* Global accessibility

S3 is one of the most widely used AWS services.

---

# Common S3 Use Cases

Amazon S3 is commonly used for:

* Application file storage
* Website assets
* Backups
* Log storage
* Data archiving
* Static website hosting
* Terraform state storage
* Disaster recovery

---

# Key S3 Concepts

## Bucket

A bucket is a top-level storage container in S3.

Example:

```text
cloudxhp-s3-lab-2026
```

Buckets must have globally unique names across AWS.

---

## Object

An object is a file stored inside a bucket.

Examples:

```text
s3-test.txt
image.jpg
backup.zip
```

---

## Object Key

The key is the object's name and path within the bucket.

Example:

```text
s3-test.txt
```

or

```text
backups/database-backup.zip
```

---

# AWS CLI S3 Commands

## List Existing Buckets

Command:

```bash
aws s3 ls
```

Purpose:

Displays all S3 buckets accessible to the AWS account.

Example Output:

```text
2026-06-10 22:56:41 cloudxhp-s3-lab-2026
```

---

## Create a Bucket

Command:

```bash
aws s3 mb s3://cloudxhp-s3-lab-2026
```

Purpose:

Creates a new S3 bucket.

Example Output:

```text
make_bucket: cloudxhp-s3-lab-2026
```

---

## Upload an Object

Create a test file:

```bash
echo "My first S3 upload" > s3-test.txt
```

Upload the file:

```bash
aws s3 cp s3-test.txt s3://cloudxhp-s3-lab-2026
```

Purpose:

Copies a local file from Linux to an S3 bucket.

Example Output:

```text
upload: ./s3-test.txt to s3://cloudxhp-s3-lab-2026/s3-test.txt
```

---

## List Objects in a Bucket

Command:

```bash
aws s3 ls s3://cloudxhp-s3-lab-2026
```

Purpose:

Displays all objects stored in the bucket.

Example Output:

```text
2026-06-10 23:00:29         19 s3-test.txt
```

---

## Download an Object

Command:

```bash
aws s3 cp s3://cloudxhp-s3-lab-2026/s3-test-2.txt downloaded.txt
```

Purpose:

Downloads an object from S3 to the local Linux machine.

Example Output:

```text
download: s3://cloudxhp-s3-lab-2026/s3-test-2.txt to ./downloaded.txt
```

Verification:

```bash
cat downloaded.txt
```

Output:

```text
S3 Lab Round 2
```

---

## Delete an Object

Command:

```bash
aws s3 rm s3://cloudxhp-s3-lab-2026/s3-test.txt
```

Purpose:

Removes an object from the bucket.

Example Output:

```text
delete: s3://cloudxhp-s3-lab-2026/s3-test.txt
```

---

# Lab Workflow

The following workflow was completed successfully:

```text
Create Bucket
      ↓
Create Local File
      ↓
Upload File
      ↓
Verify Upload
      ↓
Download File
      ↓
Verify Content
      ↓
Delete Object
```

---

# Commands Practiced

```bash
aws s3 ls

aws s3 mb s3://bucket-name

aws s3 cp file.txt s3://bucket-name

aws s3 ls s3://bucket-name

aws s3 cp s3://bucket-name/file.txt .

aws s3 rm s3://bucket-name/file.txt
```

---

# Linux vs AWS Comparison

| Linux     | AWS S3     |
| --------- | ---------- |
| Directory | Bucket     |
| File      | Object     |
| File Name | Object Key |
| cp        | aws s3 cp  |
| ls        | aws s3 ls  |
| rm        | aws s3 rm  |

---

# Real-World Cloud Engineering Usage

S3 is frequently used for:

### Backup Storage

```text
Database Backups
      ↓
S3 Bucket
```

### Application Assets

```text
Images
Videos
Documents
      ↓
S3 Bucket
```

### Infrastructure Automation

```text
Terraform State Files
      ↓
S3 Bucket
```

### Logging

```text
Application Logs
CloudTrail Logs
Server Logs
      ↓
S3 Bucket
```

---

# Troubleshooting Observation

During the lab, an object download returned:

```text
404 - Key does not exist
```

Engineering response:

1. Verify bucket contents.
2. Re-upload the object.
3. Re-test the workflow.
4. Confirm expected results.

This reinforced an important engineering principle:

```text
Trust evidence, not assumptions.
```

Always verify the current state before troubleshooting.

---

# Key Takeaways

* S3 is AWS's object storage service.
* A bucket is a storage container.
* An object is a stored file.
* Objects are managed using object keys.
* AWS CLI can create, upload, download, list, and delete S3 resources.
* S3 is a foundational AWS service used throughout cloud infrastructure.
* Verification and troubleshooting are critical engineering skills.

S3 is one of the most commonly used AWS services and is a core skill for Cloud Support Engineers, Cloud Engineers, and DevOps Engineers.

