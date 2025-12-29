# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Measuring Write Performance Under Load](#example-1) 
    - [Use Case 2 -- Diagnosing Performance Issues After Schema or Engine Changes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>InsertLatency</b> metric measures the average time taken for insert operations on an Amazon RDS instance, reported in milliseconds.
This metric is available for Aurora and other database engines that support enhanced monitoring and provides insight into write performance, storage latency, and overall database responsiveness.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: InsertLatency
* <b>Namespace</b>: AWS/RDS
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DBInstanceIdentifier
* <b>Display Name in NetBrain</b>: DB Instance Latency

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing write operation latency. Useful for identifying performance degradation, peak load periods, and the impact of schema or workload changes.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Shows the mean insert operation latency over the selected time range.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time latency troubleshooting.
    * <b>3600 seconds</b> for general performance monitoring.
    * <b>7200 seconds</b> for long-term trend evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Measuring Write Performance Under Load <a name="example-1"></a>
Tracking <b>InsertLatency</b> helps identify when the database storage layer or write throughput becomes a bottleneck during peak traffic or write-heavy workloads.


## Use Case 2: Diagnosing Performance Issues After Schema or Engine Changes <a name="example-2"></a>
An increase in insert latency may result from inefficient indexing, table structure updates, or storage I/O constraints.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS RDS Metrics Documentation
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html