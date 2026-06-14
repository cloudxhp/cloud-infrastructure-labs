# EC2 Web Server Operations Project

## Project Overview

This project demonstrates how to deploy, secure, test, monitor, and document a basic web server on AWS.

The final deployment runs on an EC2 instance inside a dedicated custom VPC public subnet, using a project-specific Security Group and CloudWatch monitoring.

---

## Architecture

```text
Internet
   ↓
Public IP Address
   ↓
Security Group: project-web-sg
   ↓
Public Subnet: enterprise-public-subnet-1a
   ↓
EC2 Instance: project-web-server
   ↓
Nginx Web Server
   ↓
CloudWatch Monitoring
```

---

## AWS Services Used

* Amazon EC2
* Amazon VPC
* Public Subnet
* Internet Gateway
* Route Table
* Security Groups
* Amazon CloudWatch
* AWS CLI
* IAM

---

## Final Project Infrastructure

| Item               | Value                       |
| ------------------ | --------------------------- |
| Instance Name      | project-web-server          |
| Instance ID        | i-04350b2e41c8f8189         |
| Instance Type      | t3.micro                    |
| Public IP          | 32.196.229.203              |
| Private IP         | 10.0.1.54                   |
| VPC Name           | custom-enterprise-vpc       |
| VPC CIDR           | 10.0.0.0/16                 |
| Public Subnet      | enterprise-public-subnet-1a |
| Public Subnet CIDR | 10.0.1.0/24                 |
| Security Group     | project-web-sg              |
| Web Server         | Nginx                       |

---

## Security Group Rules

| Rule | Port | Source            | Purpose               |
| ---- | ---: | ----------------- | --------------------- |
| SSH  |   22 | My public IP only | Secure administration |
| HTTP |   80 | 0.0.0.0/0         | Public web access     |

---

## Skills Demonstrated

* Launching EC2 instances
* Deploying Linux-based web servers
* Configuring Security Groups
* Working with public and private IP addresses
* Using a custom VPC and public subnet
* Verifying Internet Gateway and route table behavior
* Testing HTTP access with `curl`
* Monitoring EC2 metrics with CloudWatch
* Practicing AWS CLI workflows
* Documenting cloud infrastructure clearly

---

## Key Commands Used

```bash
ssh -i ~/cloud-lab-key.pem ubuntu@32.196.229.203
```

```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl status nginx
```

```bash
curl localhost
curl http://32.196.229.203
```

```bash
aws ec2 describe-instances
aws ec2 describe-security-groups
aws cloudwatch list-metrics --namespace AWS/EC2
aws cloudwatch get-metric-statistics
```

---

## Project Documentation

| File                              | Purpose                                             |
| --------------------------------- | --------------------------------------------------- |
| infrastructure-inventory.md       | Documents the original EC2 infrastructure inventory |
| dedicated-vpc-deployment.md       | Documents the dedicated custom VPC deployment       |
| cloudwatch-monitoring-evidence.md | Documents CloudWatch monitoring verification        |

---

## Lessons Learned

* EC2 instances cannot be directly moved between VPCs.
* Moving a workload to another VPC requires launching a replacement instance.
* Security Groups are tied to a specific VPC.
* A public subnet needs a route to an Internet Gateway.
* HTTP access requires port 80 to be allowed.
* SSH should be restricted to a trusted IP address.
* A deployed server should also be monitored.
* Cloud engineering work requires both implementation and documentation.

---

## Project Status

MVP complete.

The project successfully demonstrates:

* A working EC2 web server
* Deployment inside a dedicated custom VPC
* Public HTTP access
* Secure SSH access
* CloudWatch monitoring evidence
* GitHub documentation

