# AWS Security Groups

## What is a Security Group?

A Security Group is a virtual firewall that controls inbound and outbound traffic for AWS resources such as EC2 instances.

Security Groups are stateful.

---

## Security Group Components

### Inbound Rules

Control traffic entering an EC2 instance.

Examples:

- SSH (22)
- HTTP (80)
- HTTPS (443)

---

### Outbound Rules

Control traffic leaving an EC2 instance.

Default AWS behavior allows all outbound traffic.

---

## Example Security Group Rules

### SSH

TCP 22

Used for remote administration.

### HTTP

TCP 80

Used for web traffic.

### HTTPS

TCP 443

Used for encrypted web traffic.

---

## My Lab Security Group

Group Name:

launch-wizard-3

Group ID:

sg-01f9de97b3f5e6001

Inbound Rules:

- TCP 22 (SSH)
- TCP 80 (HTTP)

Outbound Rules:

- All traffic allowed

---

## Security Group vs Traditional Firewall

Security Groups act as virtual firewalls attached directly to AWS resources.

They determine which traffic is allowed to enter or leave an EC2 instance.

---

## Stateful Behavior

Security Groups are stateful.

If inbound traffic is allowed:

Client → EC2

the response traffic is automatically allowed back.

No separate outbound rule is required for the return traffic.

---

## Troubleshooting Checklist

1. Verify service is running

systemctl status nginx

2. Verify application is listening

ss -tulpn

3. Test locally

curl localhost

4. Verify Security Group rules

5. Verify Route Table

6. Verify Public IP

---

## Commands Used

aws ec2 describe-security-groups

aws ec2 describe-security-groups --group-ids sg-01f9de97b3f5e6001
