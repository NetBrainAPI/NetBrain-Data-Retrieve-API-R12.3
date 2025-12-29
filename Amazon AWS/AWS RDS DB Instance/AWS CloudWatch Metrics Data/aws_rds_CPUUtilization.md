# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Performance Bottlenecks](#example-1) 
    - [Use Case 2 -- Scaling and Capacity Planning](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>CPUUtilization</b> metric measures the percentage of CPU resources currently being used by an Amazon RDS instance.
Monitoring this metric helps ensure that the database instance has sufficient compute capacity to handle workloads and can reveal performance bottlenecks caused by high CPU consumption.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CPUUtilization
* <b>Namespace</b>: AWS/RDS
* <b>Unit / Stat</b>: Maximum
* <b>Dimension</b>: DBInstanceIdentifier
* <b>Display Name in NetBrain</b>: DB Instance CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used to analyze CPU usage. Useful for identifying load peaks, tuning performance, and diagnosing query or workload inefficiencies.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Maximum.
  * <b>Maximum</b>: Indicates the highest CPU usage percentage recorded within the specified time window.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time CPU spike detection.
    * <b>3600 seconds</b> for standard performance insights.
    * <b>7200 seconds</b> for long-term capacity planning.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Performance Bottlenecks <a name="example-1"></a>
High CPU utilization may indicate inefficient queries, missing indexes, or insufficient instance class sizing.

## Use Case 2: Scaling and Capacity Planning <a name="example-2"></a>
Monitoring CPU peaks helps determine when to scale up the RDS instance or optimize the workload to avoid throttling or degraded performance.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS RDS Metrics Documentation
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html
