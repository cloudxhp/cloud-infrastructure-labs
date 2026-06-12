# EC2 Web Server Operations Project

## Project Overview

This project demonstrates how to deploy, access, troubleshoot, and document a basic web server running on an AWS EC2 instance.

The purpose of this project is to practice real cloud operations skills using AWS, Linux, networking, security groups, and monitoring concepts.

---

## Project Goals

* Launch and manage an EC2 instance
* Connect to the server using SSH
* Install and verify a web server
* Configure Security Group access
* Test HTTP connectivity
* Use Linux troubleshooting commands
* Review CloudWatch monitoring metrics
* Document the infrastructure workflow

---

## AWS Services Used

* Amazon EC2
* Security Groups
* Amazon VPC
* Internet Gateway
* Route Tables
* Amazon CloudWatch
* Amazon S3
* AWS CLI
* IAM

---

## Linux Skills Used

* SSH access
* Package installation
* Service status checks
* Port inspection
* Network testing
* Log review
* File editing
* Command-line documentation

---

## Architecture

```text
Internet
   ↓
Public IP Address
   ↓
Security Group
   ↓
EC2 Instance
   ↓
Web Server
   ↓
CloudWatch Monitoring
```

---

## Key Concepts Practiced

### EC2

Amazon EC2 provides virtual servers in the cloud. In this project, EC2 was used to host a basic web server.

### Security Groups

Security Groups control inbound and outbound traffic. HTTP traffic requires port 80 to be open.

### Public vs Private IP

The public IP allows internet access to the instance. The private IP is used inside the AWS VPC network.

### Web Server

A web server listens on a network port and responds to HTTP requests.

### CloudWatch

CloudWatch provides monitoring metrics such as CPU utilization, network traffic, and instance health checks.

---

## Troubleshooting Workflow

When testing web server access, the following troubleshooting process was used:

```text
Check EC2 instance state
        ↓
Check Security Group rules
        ↓
Check web server status
        ↓
Check listening ports
        ↓
Test localhost
        ↓
Test public IP
        ↓
Review CloudWatch metrics
```

---

## Commands Practiced

```bash
ssh -i key.pem ubuntu@public-ip
```

```bash
sudo systemctl status nginx
```

```bash
sudo ss -tulpn | grep :80
```

```bash
curl localhost
```

```bash
curl http://public-ip
```

```bash
aws ec2 describe-instances
```

```bash
aws ec2 describe-security-groups
```

```bash
aws cloudwatch list-metrics --namespace AWS/EC2
```

---

## Lessons Learned

* A running EC2 instance does not automatically mean an application is reachable.
* Security Groups must allow the correct inbound ports.
* A web server must be running and listening on the expected port.
* `curl localhost` helps confirm whether the application works locally.
* `ss -tulpn` helps verify which services are listening.
* CloudWatch provides visibility into EC2 performance and health.
* Troubleshooting should be done layer by layer instead of guessing.

---

## Cloud Engineering Relevance

This project reflects real Cloud Support and Cloud Engineering tasks:

* Deploying cloud infrastructure
* Connecting to Linux servers
* Managing web services
* Troubleshooting connectivity
* Understanding AWS networking
* Reviewing monitoring metrics
* Documenting technical work clearly

---

## Status

Project in progress.

Next improvements:

* Add screenshots
* Add exact EC2 configuration details
* Add CloudWatch metric examples
* Add S3 backup or documentation storage step
* Add final cleanup steps
