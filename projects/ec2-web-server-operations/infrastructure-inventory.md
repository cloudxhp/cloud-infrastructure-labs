# Infrastructure Inventory

## Project

EC2 Web Server Operations Project

---

## Active Project Instance

| Item           | Value                    |
| -------------- | ------------------------ |
| Instance Name  | linux-lab-server         |
| Instance ID    | i-014482e970e289d1b      |
| Instance Type  | t3.micro                 |
| Instance State | running                  |
| Public IP      | 54.91.18.82              |
| Private IP     | 172.31.24.70             |
| VPC ID         | vpc-08631bf427256dfbe    |
| Subnet ID      | subnet-03340e3c9a9669a4d |
| Security Group | launch-wizard-1          |

---

## Secondary Running Instance

| Item           | Value                    |
| -------------- | ------------------------ |
| Instance Name  | linux-sandbox            |
| Instance ID    | i-03b9be539ad1cf384      |
| Instance Type  | t3.micro                 |
| Instance State | running                  |
| Public IP      | 3.82.12.149              |
| Private IP     | 172.31.42.28             |
| VPC ID         | vpc-08631bf427256dfbe    |
| Subnet ID      | subnet-0dc65a9b86b257394 |
| Security Group | launch-wizard-3          |

---

## Current Infrastructure Notes

* The project web server will use the `linux-lab-server` instance.
* The instance is running inside the default VPC.
* The instance has both a public IP and private IP.
* The public IP is used for internet access.
* The private IP is used inside the AWS VPC network.
* Security Group rules control which network traffic can reach the instance.
* CloudWatch provides monitoring metrics for the EC2 instance.

---

## Cost Awareness Note

There are currently two running EC2 instances.

Before ending the lab session, unused resources should be reviewed to avoid unnecessary AWS charges.
