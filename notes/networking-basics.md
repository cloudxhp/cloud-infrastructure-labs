# Networking Basics

## IP Addresses

### Private IP
Used inside a home or company network.

Examples:
- 192.168.x.x
- 10.x.x.x
- 172.x.x.x

### Public IP
Visible on the internet and used for external communication.

---

## DNS

DNS (Domain Name System) translates domain names into IP addresses.

Example:

google.com → IP address

DNS works like the internet's phonebook.

---

## Ports

Ports allow multiple services to run on one machine.

Common Ports:
- 22 → SSH
- 80 → HTTP
- 443 → HTTPS

Think of:
- IP address = apartment building
- Port = apartment number

---

## HTTP

HTTP (HyperText Transfer Protocol) is used for unencrypted web traffic.

Example:
- http://example.com

---

## HTTPS

HTTPS is encrypted and secure web traffic using TLS encryption.

Example:
- https://example.com

---

# Commands Learned

## ping
Tests network connectivity.

```bash
ping google.com
```

---

## curl
Retrieves data from servers.

```bash
curl ifconfig.me
```

Shows public IP address.

---

## sudo
Runs commands with administrative privileges.

```bash
sudo apt update
```

---

## nslookup
Queries DNS information.

```bash
nslookup google.com
```
