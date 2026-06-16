# Dedicated VPC Web Server Deployment

## Project

EC2 Web Server Operations Project

---

## Deployment Summary

This phase moved the project web server from the default VPC approach to a dedicated custom VPC environment.

A new EC2 instance was launched inside the custom VPC public subnet and configured as a web server using Nginx.

---

## Custom VPC Details

| Item                | Value                        |
| ------------------- | ---------------------------- |
| VPC Name            | custom-enterprise-vpc        |
| VPC ID              | vpc-0e155d00ed6c17782        |
| VPC CIDR            | 10.0.0.0/16                  |
| Public Subnet       | enterprise-public-subnet-1a  |
| Public Subnet ID    | subnet-0e24dcfcf2223b035     |
| Public Subnet CIDR  | 10.0.1.0/24                  |
| Private Subnet      | enterprise-private-subnet-1a |
| Private Subnet CIDR | 10.0.0.0/24                  |
| Internet Gateway    | enterprise-igw               |
| Route Table         | enterprise-public-rt         |

---

## EC2 Instance Details

| Item           | Value                    |
| -------------- | ------------------------ |
| Instance Name  | project-web-server       |
| Instance ID    | i-04350b2e41c8f8189      |
| Instance Type  | t3.micro                 |
| Public IP      | 32.196.229.203           |
| Private IP     | 10.0.1.54                |
| VPC ID         | vpc-0e155d00ed6c17782    |
| Subnet ID      | subnet-0e24dcfcf2223b035 |
| Security Group | project-web-sg           |

---

## Lab IP Address Note

The public IP address shown in this project is a lab snapshot.

Because this EC2 instance uses an auto-assigned public IPv4 address, the public IP may change if the instance is stopped and started again.

The project remains valid because the documented architecture, deployment process, security group configuration, and monitoring workflow are the main learning outcomes.

## Security Group Details

| Rule | Port | Source            | Purpose               |
| ---- | ---: | ----------------- | --------------------- |
| SSH  |   22 | My public IP only | Secure administration |
| HTTP |   80 | 0.0.0.0/0         | Public web access     |

---

## Web Server Setup

Nginx was installed on the EC2 instance.

Commands used:

```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl status nginx
```

Local test from inside EC2:

```bash
curl localhost
```

External test from WSL:

```bash
curl http://32.196.229.203
```

The external test returned the default Nginx welcome page, confirming that the web server is reachable from the internet.

---

## Architecture

```text
Internet
   ↓
Public IP Address
   ↓
Security Group allowing HTTP port 80
   ↓
Public Subnet in Custom VPC
   ↓
EC2 Instance
   ↓
Nginx Web Server
```

---

## Key Lessons Learned

* EC2 instances cannot be directly moved between VPCs.
* To move a workload to a different VPC, a replacement instance must be created in the target VPC.
* Security Groups are tied to a specific VPC.
* A public subnet needs a route to an Internet Gateway.
* Auto-assign public IP must be enabled or manually assigned for internet access.
* HTTP access requires port 80 to be allowed in the Security Group.
* Successful `curl` output confirms that networking, security, and web server layers are working together.

---

## Result

The project web server is now running successfully inside a dedicated custom VPC.
