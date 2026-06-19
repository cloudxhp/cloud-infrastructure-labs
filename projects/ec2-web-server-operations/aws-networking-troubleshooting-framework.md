# AWS Networking Troubleshooting Framework

## Purpose

This document contains steps to troubleshoot AWS networking issues for an EC2 web server.

The goal is to understand why a website may not load even when the EC2 instance appears to be running.

---

## Troubleshooting Order

1. Check if the EC2 instance is running.
2. Check if Nginx is running.
3. Check if the instance has a public IP address.
4. Check if the Security Group allows HTTP traffic on port 80.
5. Check if the subnet route table has `0.0.0.0/0 → Internet Gateway`.
6. Check if the Internet Gateway is attached to the VPC.
7. Check if the Network ACL allows traffic both ways.

---

## Key Points

1. Route tables route traffic through the Internet Gateway when they have `0.0.0.0/0 → Internet Gateway`.

2. Security Groups are stateful. If traffic is allowed in, response traffic is automatically allowed out.

3. Network ACLs are stateless. Traffic must be allowed both inbound and outbound for the website to load.

4. Databases contain sensitive data. Database access should not be open to `0.0.0.0/0`. Only approved web servers or application servers should be allowed through Security Group rules.

---

## My Project Example

### Scenario

The EC2 instance has a public IP address, Nginx is running, and the EC2 instance is running, but the website does not load from my laptop.

### Checks

* Check if the Security Group allows HTTP traffic on port 80.
* Check if the route table has `0.0.0.0/0 → Internet Gateway`.
* Check if the Internet Gateway is attached to the VPC.
* Check if the Network ACL allows traffic both ways.

---

## Simple Memory Rule

* Public IP = internet address
* Route Table = road
* Internet Gateway = doorway to the internet
* Security Group = gate at the EC2 instance
* Network ACL = checkpoint at the subnet level
* Nginx = service answering the request
