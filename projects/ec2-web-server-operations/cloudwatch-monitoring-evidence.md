# CloudWatch Monitoring Evidence

## Project

EC2 Web Server Operations Project

---

## Monitored Instance

| Item             | Value                 |
| ---------------- | --------------------- |
| Instance Name    | project-web-server    |
| Instance ID      | i-04350b2e41c8f8189   |
| Public IP        | 32.196.229.203        |
| VPC              | custom-enterprise-vpc |
| Metric Namespace | AWS/EC2               |

---

## Metric Verified

| Metric         | Purpose                           |
| -------------- | --------------------------------- |
| CPUUtilization | Measures EC2 CPU usage percentage |

---

## Command Used to Confirm Metric Exists

```bash
aws cloudwatch list-metrics \
--namespace AWS/EC2 \
--metric-name CPUUtilization \
--dimensions Name=InstanceId,Value=i-04350b2e41c8f8189 \
--output table
```

Result confirmed that CloudWatch has a `CPUUtilization` metric for the project EC2 instance.

---

## Command Used to Retrieve CPU Data

```bash
aws cloudwatch get-metric-statistics \
--namespace AWS/EC2 \
--metric-name CPUUtilization \
--dimensions Name=InstanceId,Value=i-04350b2e41c8f8189 \
--statistics Average \
--start-time $(date -u -d '2 hours ago' +%Y-%m-%dT%H:%M:%SZ) \
--end-time $(date -u +%Y-%m-%dT%H:%M:%SZ) \
--period 300 \
--output table
```

---

## Sample CPU Datapoints

| Timestamp                 | Average CPU | Unit    |
| ------------------------- | ----------: | ------- |
| 2026-06-14T05:24:00+00:00 |        0.07 | Percent |
| 2026-06-14T05:19:00+00:00 |        0.10 | Percent |
| 2026-06-14T05:14:00+00:00 |        3.47 | Percent |

---

## Interpretation

The EC2 instance is running normally with low CPU usage.

Low CPU usage is expected because this server is currently serving a basic Nginx default page with minimal traffic.

---

## Cloud Engineering Relevance

CloudWatch monitoring helps engineers:

* Confirm that infrastructure is reporting metrics
* Check server performance
* Troubleshoot slow applications
* Detect unhealthy instances
* Create alarms for production systems

---

## Key Lesson

A cloud server should not only be deployed successfully. It should also be monitored.

This project confirms both:

* The web server is reachable from the internet
* CloudWatch is collecting performance metrics for the instance
