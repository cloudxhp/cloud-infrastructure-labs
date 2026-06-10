# Linux Ports and Services

## Objective

Learn how Linux services communicate over networks, how applications listen for connections, and how to identify active services using networking tools.

These concepts are fundamental for:

* Linux Administration
* Cloud Support Engineering
* AWS EC2 Troubleshooting
* DevOps
* Web Server Management
* Containerized Applications

---

# Understanding Ports and Services

A service is an application running on a system that performs a specific function.

Examples:

| Service | Purpose               |
| ------- | --------------------- |
| SSH     | Remote administration |
| Nginx   | Web server            |
| Apache  | Web server            |
| MySQL   | Database server       |
| DNS     | Name resolution       |

Services communicate through network ports.

A port acts like a numbered doorway through which network traffic enters or leaves a system.

---

# Common Network Ports

| Port | Service                 |
| ---- | ----------------------- |
| 22   | SSH                     |
| 53   | DNS                     |
| 80   | HTTP                    |
| 443  | HTTPS                   |
| 3306 | MySQL                   |
| 5432 | PostgreSQL              |
| 8080 | Common application port |

Cloud Engineers frequently recognize these ports during troubleshooting.

---

# Viewing Active Services

## Command

```bash
ss -tulpn
```

## Purpose

Displays active network sockets and listening services.

## Options

| Option | Meaning                          |
| ------ | -------------------------------- |
| -t     | TCP sockets                      |
| -u     | UDP sockets                      |
| -l     | Listening sockets                |
| -p     | Process information              |
| -n     | Show numeric addresses and ports |

---

# Example Output

```text
tcp LISTEN 0 1 0.0.0.0:8080 0.0.0.0:* users:(("nc",pid=3492,fd=3))
```

---

# Understanding the Output

## TCP

```text
tcp
```

Indicates the service is using the TCP protocol.

TCP is commonly used by:

* SSH
* HTTP
* HTTPS
* Databases

TCP provides reliable communication between systems.

---

## LISTEN

```text
LISTEN
```

Means the application is waiting for incoming connections.

The service is ready to accept traffic.

---

## Port Number

```text
8080
```

Represents the communication endpoint being used.

Applications listen on specific ports so clients know where to connect.

---

## Process Information

```text
users:(("nc",pid=3492,fd=3))
```

Provides:

* Process name
* Process ID (PID)
* File descriptor

This information is valuable when identifying which application owns a port.

---

# Understanding Network Addresses

## Localhost

```text
127.0.0.1
```

Meaning:

```text
This machine only
```

Services bound to localhost cannot be reached by other systems.

Example:

```text
127.0.0.1:8080
```

Accessible only from the local machine.

---

## All Interfaces

```text
0.0.0.0
```

Meaning:

```text
All available network interfaces
```

Example:

```text
0.0.0.0:8080
```

Allows connections from external systems if firewalls and security rules permit.

---

# Filtering Listening Services

## Command

```bash
ss -tulpn | grep LISTEN
```

## Purpose

Displays only services actively waiting for incoming connections.

Useful when identifying:

* Running services
* Open ports
* Active applications

---

# Creating a Test Service

## Install Netcat

```bash
sudo apt install netcat-openbsd -y
```

Netcat is a lightweight networking utility commonly used for testing and troubleshooting.

---

## Create a Listening Service

```bash
nc -lvnp 8080
```

## Purpose

Creates a simple TCP listener on port 8080.

Options:

| Option | Meaning        |
| ------ | -------------- |
| -l     | Listen mode    |
| -v     | Verbose output |
| -n     | No DNS lookups |
| -p     | Specify port   |

---

## Verify Listener

```bash
ss -tulpn | grep 8080
```

Expected output:

```text
tcp LISTEN 0 1 0.0.0.0:8080
```

This confirms:

* Application is running
* Port is open
* Service is listening for connections

---

# Real-World Troubleshooting Workflow

When an application is unavailable:

## Step 1

Verify service status.

Example:

```bash
systemctl status nginx
```

---

## Step 2

Verify listening ports.

```bash
ss -tulpn
```

---

## Step 3

Confirm expected port exists.

Examples:

```text
22
80
443
8080
```

---

## Step 4

Test connectivity.

```bash
curl localhost
```

or

```bash
curl http://server-ip
```

---

## Step 5

Investigate network controls.

Check:

* Firewall rules
* AWS Security Groups
* Route tables
* DNS records

---

# AWS Cloud Engineering Relevance

Ports and services directly relate to AWS infrastructure.

| Linux Concept   | AWS Equivalent           |
| --------------- | ------------------------ |
| Listening Port  | Open Application Port    |
| SSH Service     | EC2 Remote Access        |
| Port 80         | Web Application Traffic  |
| Port 443        | Secure HTTPS Traffic     |
| Open Port       | Security Group Rule      |
| Running Service | Application Availability |

Example:

If an EC2-hosted website is unavailable:

1. Verify Nginx or Apache is running.
2. Verify port 80 or 443 is listening.
3. Verify Security Groups allow traffic.
4. Verify the application responds correctly.

---

# Key Takeaways

* Services communicate through ports.
* Listening services accept incoming connections.
* `ss -tulpn` displays active network services.
* `127.0.0.1` means local access only.
* `0.0.0.0` means all network interfaces.
* Netcat can create a temporary listening service for testing.
* Troubleshooting should follow a structured process:

  * Verify service
  * Verify port
  * Verify connectivity
  * Verify network controls

Understanding ports and services is a foundational skill for Linux administration, AWS troubleshooting, Cloud Support, and Cloud Engineering.
