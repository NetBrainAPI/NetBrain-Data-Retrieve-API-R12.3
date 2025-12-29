# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Cluster Memory Pressure](#example-1) 
    - [Use Case 2 -- Optimizing Workload Placement](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>ECS Cluster Memory Utilization</b> metric measures the overall percentage of memory consumed by all running tasks and services within an Amazon ECS cluster. Monitoring this metric is crucial for identifying memory pressure, optimizing container workloads, and ensuring the cluster has adequate capacity to meet application demands.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: MemoryUtilization
* <b>Namespace</b>: AWS/ECS
* <b>Unit / Stat</b>: Percent
* <b>Dimension</b>: ClusterName
* <b>Display Name in NetBrain</b>: Memory Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for evaluating memory usage trends within the ECS cluster. Helps identify periods of high memory consumption or underutilization.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Percent.
  * <b>Percent</b>: Represents the percentage of total cluster memory capacity used during the selected timeframe.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed memory monitoring during sudden workload surges.
    * <b>3600 seconds</b> for hourly memory trend visibility.
    * <b>7200 seconds</b> for long-term capacity and scaling analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Cluster Memory Pressure <a name="example-1"></a>
High <b>MemoryUtilization</b> indicates memory bottlenecks and may require scaling services, increasing instance sizes, or optimizing container memory limits.


## Use Case 2: Optimizing Workload Placement <a name="example-2"></a>
Memory usage patterns help identify inefficient tasks, memory leaks, or imbalanced workloads, supporting better ECS task placement and cluster tuning.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS ECS Memory Utilization Metric Documentation
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cloudwatch-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html