# Linux Networking Fundamentals

## Objective

Learn the foundational Linux networking commands used to troubleshoot connectivity, DNS, routing, and application access. These concepts directly apply to AWS networking services such as VPCs, Subnets, Route Tables, Security Groups, Load Balancers, and DNS.

---

# Why Networking Matters

Every cloud resource communicates over a network.

A Cloud Engineer must be able to answer questions such as:

* Does the machine have an IP address?
* Can it reach the internet?
* Is DNS working?
* Is traffic being routed correctly?
* Is the application accessible?

Linux networking commands provide the tools needed to answer these questions.

---

# 1. View Network Interfaces

## Command

```bash
ip addr
```

## Purpose

Displays network interfaces and assigned IP addresses.

## Example

```text
eth0
172.23.54.32/20
```

## Troubleshooting Use

Use this command to verify:

* Network interface exists
* Interface is active
* IP address has been assigned

### Common Question

"Does this machine have a valid IP address?"

---

# 2. View Routing Table

## Command

```bash
ip route
```

## Purpose

Displays how network traffic leaves the machine.

## Example

```text
default via 172.23.48.1 dev eth0
172.23.48.0/20 dev eth0
```

## Key Concepts

### Default Route

```text
default via 172.23.48.1
```

The gateway used when traffic is destined for external networks.

### Connected Network

```text
172.23.48.0/20
```

Traffic within this network is sent directly.

## Troubleshooting Use

Use this command when:

* Internet access is unavailable
* Traffic is being routed incorrectly
* Gateway configuration must be verified

### Common Question

"Where is this machine sending traffic?"

---

# 3. View Hostname

## Command

```bash
hostname
```

## Purpose

Displays the system hostname.

## Example

```text
DESKTOP-A7I7PPG
```

## Troubleshooting Use

Useful when managing multiple systems and confirming the current machine.

### Common Question

"Which system am I currently logged into?"

---

# 4. Verify DNS Configuration

## Command

```bash
cat /etc/resolv.conf
```

## Purpose

Displays configured DNS servers.

## Example

```text
nameserver 172.23.48.1
```

## Key Concept

DNS translates:

```text
google.com
```

into:

```text
142.251.x.x
```

## Troubleshooting Use

Use when:

* Websites cannot be reached by name
* DNS resolution fails
* Applications cannot locate external services

### Common Question

"Which DNS server is this machine using?"

---

# 5. Test Network Connectivity

## Command

```bash
ping -c 4 google.com
```

## Purpose

Tests basic network connectivity.

## Example

```text
4 packets transmitted
4 received
0% packet loss
```

## Key Metrics

### Packet Loss

```text
0%
```

Indicates reliable communication.

### Latency

```text
52 ms
```

Represents network response time.

## Troubleshooting Use

Use when verifying:

* Internet access
* Host reachability
* Basic network connectivity

### Common Question

"Can this machine reach another system?"

---

# 6. Test DNS Resolution

## Command

```bash
nslookup google.com
```

## Purpose

Queries DNS directly.

## Example

```text
Name: google.com
Address: 142.251.x.x
```

## Troubleshooting Use

Use when:

* Websites fail to load
* DNS problems are suspected
* Hostname resolution must be verified

### Common Question

"Can DNS successfully resolve this hostname?"

---

# 7. Test Application Connectivity

## Command

```bash
curl -I https://google.com
```

## Purpose

Retrieves HTTP response headers.

## Example

```text
HTTP/2 301
location: https://www.google.com/
```

## Common Response Codes

### 200

```text
Success
```

### 301

```text
Permanent Redirect
```

### 403

```text
Access Denied
```

### 404

```text
Resource Not Found
```

### 500

```text
Server Error
```

## Troubleshooting Use

Use when verifying:

* Website availability
* Web server responses
* Application accessibility

### Common Question

"Is the application responding correctly?"

---

# Troubleshooting Workflow

A Cloud Engineer typically follows this order:

## Step 1

Check IP Address

```bash
ip addr
```

## Step 2

Check Routing

```bash
ip route
```

## Step 3

Check DNS Configuration

```bash
cat /etc/resolv.conf
```

## Step 4

Test Connectivity

```bash
ping google.com
```

## Step 5

Test DNS Resolution

```bash
nslookup google.com
```

## Step 6

Test Application Access

```bash
curl -I https://google.com
```

---

# Real-World Cloud Engineering Relevance

Linux Networking Concepts Map Directly To AWS Services:

| Linux Concept        | AWS Equivalent                     |
| -------------------- | ---------------------------------- |
| IP Address           | EC2 Private IP                     |
| Network Interface    | Elastic Network Interface (ENI)    |
| Default Gateway      | Route Table                        |
| DNS Server           | Route 53 / Amazon DNS              |
| Connectivity Testing | Security Group Troubleshooting     |
| Application Access   | Load Balancer / Web Server Testing |

---

# Key Takeaways

* Every system requires a valid IP address.
* Routing determines where traffic is sent.
* DNS converts hostnames into IP addresses.
* Ping verifies network connectivity.
* Nslookup verifies DNS functionality.
* Curl verifies application accessibility.
* Networking troubleshooting should follow a structured sequence.

These commands form the foundation of Linux administration, Cloud Support, AWS troubleshooting, and Cloud Engineering.

