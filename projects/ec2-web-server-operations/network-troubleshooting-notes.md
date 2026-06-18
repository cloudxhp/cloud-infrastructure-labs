# Network Troubleshooting Notes

If curl localhost works inside EC2, that means the web server is working locally.

If the ebsite still doesn't load check the following:

- instance has public IP?
- Route table has 0.0.0.0/0 -> Internet Gateway?
- Security Group is set to allow HTTP traffic on port 80?
- Is the Internet Gateway attached to the VPC?

Public IP gives the server an internet address.
