# EC2 Operations Notes

## Objective

Launch, access, and administer an AWS EC2 instance using Linux and SSH while 
documenting core infrastructure operations concepts.

---

# EC2 Overview

Amazon EC2 (Elastic Compute Cloud) provides virtual servers in the AWS cloud.

EC2 instances can be used to:

* Host websites
* Run applications
* Perform automation tasks
* Execute scripts
* Build cloud infrastructure environments

---

# EC2 Launch Process

### 1. Launch Instance

AWS Console:

```text
EC2 → Launch Instance
```

Selections:

* Ubuntu Server
* t3.micro
* Key Pair
* Security Group
* Default VPC

---

### 2. Security Group Configuration

Security Groups act as virtual firewalls.

Inbound Rules:

| Type  | Port | Purpose               |
| ----- | ---- | --------------------- |
| SSH   | 22   | Remote administration |
| HTTP  | 80   | Web traffic           |
| HTTPS | 443  | Secure web traffic    |

Key Learning:

```text
If a port is not allowed in the Security Group,
traffic cannot reach the EC2 instance.
```

---

# SSH Remote Access

SSH allows secure remote administration of Linux servers.

Connection command:

```bash
ssh -i cloud-lab-key.pem ubuntu@<public-ip>
```

Components:

* ssh = Secure Shell
* -i = Identity file (private key)
* ubuntu = Username
* Public IP = Address of EC2 instance

---

# Linux Administration Commands

### User Information

```bash
whoami
pwd
hostname
```

### System Information

```bash
free -h
df -h
uname -a
```

### Network Information

```bash
curl ifconfig.me
```

### Process Inspection

```bash
ps aux
```

---

# Web Server Installation

Installed Apache:

```bash
sudo apt update
sudo apt install apache2 -y
```

Attempted to start Apache:

```bash
sudo systemctl start apache2
```

---

# Troubleshooting Example

Apache failed to start.

Investigated:

```bash
sudo systemctl status apache2
```

Discovered:

```text
Address already in use
```

Further investigation:

```bash
sudo lsof -i :80
```

Result:

```text
nginx was already listening on port 80
```

Key Lesson:

```text
Only one service can bind to the same port
at a time.
```

Because nginx was already using port 80, Apache could not start.

---

# AWS Concepts Learned

## Public IP

Internet-accessible IP address assigned to an EC2 instance.

Example:

```text
54.x.x.x
```

---

## Private IP

Internal AWS network address.

Example:

```text
172.31.x.x
```

Used for communication within AWS networks.

---

## Security Groups

Control inbound and outbound traffic.

Common Ports:

| Port | Protocol |
| ---- | -------- |
| 22   | SSH      |
| 80   | HTTP     |
| 443  | HTTPS    |

---

# EC2 Lifecycle States

Instances move through different states:

```text
Pending
Running
Stopping
Stopped
Terminated
```

Important:

```text
Terminated instances cannot be recovered.
```

---

# Key Takeaways

* Successfully launched an EC2 instance.
* Connected remotely using SSH.
* Administered a Linux server.
* Installed software packages.
* Investigated service failures.
* Diagnosed port conflicts.
* Worked with Security Groups.
* Used Linux troubleshooting commands.
* Gained practical experience managing cloud infrastructure.

---

# Skills Practiced

* AWS EC2
* Linux Administration
* SSH
* Security Groups
* Process Management
* Service Troubleshooting
* Networking Fundamentals
* Infrastructure Documentation
* Git & GitHub Workflow

