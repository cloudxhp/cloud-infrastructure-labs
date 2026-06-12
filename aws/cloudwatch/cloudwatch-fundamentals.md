# AWS CloudWatch Fundamentals

## What is CloudWatch?

Amazon CloudWatch is AWS's monitoring and observability service.

It collects:

- Metrics
- Logs
- Events

from AWS resources and applications.

---

## Why CloudWatch Matters

CloudWatch helps engineers:

- Monitor infrastructure
- Detect issues
- Troubleshoot problems
- Create alerts
- Track performance

---

## Common EC2 Metrics

### CPUUtilization

Measures CPU usage percentage.

Used to identify overloaded instances.

---

### NetworkIn

Measures incoming network traffic.

Useful for monitoring application usage.

---

### NetworkOut

Measures outgoing network traffic.

Useful for tracking responses sent by applications.

---

### StatusCheckFailed

Indicates instance health issues.

Value:

0 = Healthy

1 = Problem Detected

---

## Storage Metrics

Examples:

- EBSReadBytes
- EBSWriteBytes
- EBSReadOps
- EBSWriteOps

Used to monitor disk activity.

---

## CloudWatch Use Cases

### Performance Monitoring

Monitor CPU, memory, disk, and network activity.

### Troubleshooting

Investigate service outages and performance issues.

### Alerting

Create alarms when thresholds are exceeded.

Example:

CPUUtilization > 80%

### Capacity Planning

Track resource usage trends over time.

---

## Commands Used

aws cloudwatch list-metrics --max-items 20

aws cloudwatch list-metrics --namespace AWS/EC2

---

## Key Takeaways

- CloudWatch is AWS's monitoring platform.
- Metrics provide visibility into resource performance.
- CPUUtilization is one of the most important EC2 metrics.
- NetworkIn and NetworkOut measure traffic.
- StatusCheckFailed helps identify unhealthy instances.
- Monitoring is essential for cloud operations and troubleshooting.
