# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Assessing Cluster Resource Utilization](#example-1) 
    - [Use Case 2 -- Troubleshooting Application Performance Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>ECS Cluster CPU Utilization</b> metric measures the overall percentage of CPU resources consumed by all running tasks and services within an Amazon ECS cluster. Monitoring this metric is essential for assessing cluster performance, identifying resource saturation, and ensuring efficient scaling of container workloads.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CPUUtilization
* <b>Namespace</b>: AWS/ECS
* <b>Unit / Stat</b>: Percent
* <b>Dimension</b>: ClusterName
* <b>Display Name in NetBrain</b>: CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range used to analyze ECS cluster compute utilization trends. Useful for performance analysis, capacity planning, and workload optimization.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Percent.
  * <b>Percent</b>: Indicates the percentage of total CPU capacity used during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed CPU monitoring during load spikes.
    * <b>3600 seconds</b> for standard hourly utilization visibility.
    * <b>7200 seconds</b> for long-term scaling and capacity analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Assessing Cluster Resource Utilization <a name="example-1"></a>
Monitoring <b>CPUUtilization</b> helps ensure that the ECS cluster has adequate compute capacity. High sustained CPU levels may indicate the need to scale tasks, services, or underlying EC2 instances.

## Use Case 2: Troubleshooting Application Performance Issues <a name="example-2"></a>
Sudden increases or fluctuations in CPU usage may point to inefficient container workloads, misconfigurations, or unexpected traffic surges. This metric helps identify when workloads require optimization.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS ECS CPU Utilization Metric Documentation
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cloudwatch-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html