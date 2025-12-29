# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Query and Workload Performance](#example-1) 
    - [Use Case 2 -- Detecting Resource Saturation and Performance Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Neptune Cluster CPU Utilization</b> metric measures the average percentage of CPU resources consumed by an Amazon Neptune database cluster. Monitoring this metric is essential for understanding workload performance, identifying processing bottlenecks, and ensuring that the cluster has adequate compute capacity to efficiently handle graph queries and transactions.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CPUUtilization
* <b>Namespace</b>: AWS/Neptune
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DBClusterIdentifier
* <b>Display Name in NetBrain</b>: CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the timeframe for analyzing CPU usage patterns across the Neptune cluster. Helps identify high-load periods, performance issues, or scaling needs.
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Indicates the mean CPU utilization percentage over the specified analysis window.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed CPU performance monitoring.
    * <b>3600 seconds</b> for standard cluster utilization analysis.
    * <b>7200 seconds</b> for long-term workload evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Query and Workload Performance <a name="example-1"></a>
Tracking <b>CPUUtilization</b> helps identify when Neptune instances are under heavy computational load, which may require query optimization, additional read replicas, or instance scaling.


## Use Case 2: Detecting Resource Saturation and Performance Issues <a name="example-2"></a>
Consistently high CPU usage can indicate inefficient queries, intensive graph traversals, or spikes in concurrent workloads. This metric supports diagnosing and resolving such performance bottlenecks.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Neptune Metrics Documentation
https://docs.aws.amazon.com/neptune/latest/userguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html