# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Performance Monitoring and Scaling Decisions](#example-1) 
    - [Use Case 2 -- Identifying Inefficient Queries or Workloads](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Instance CPU Utilization</b> metric tracks the percentage of CPU resources consumed by each Amazon DocumentDB instance over a given period. Monitoring CPU utilization is crucial for understanding workload performance, identifying processing bottlenecks, and determining when to scale instance classes or optimize queries.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CPUUtilization
* <b>Namespace</b>: AWS/DocDB
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DBInstanceIdentifier
* <b>Display Name in NetBrain</b>: Instance CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing CPU performance trends. Helps identify peak usage periods and potential resource saturation.
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Shows the mean CPU consumption for the selected time window
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for fine-grained CPU performance monitoring.
    * <b>3600 seconds</b> for standard hourly CPU visibility.
    * <b>7200 seconds</b> for long-term utilization trends.

# Use Cases Example <a name="example"></a>
## Use Case 1: Performance Monitoring and Scaling Decisions <a name="example-1"></a>
Tracking <b>CPUUtilization</b> helps determine when an instance is consistently under heavy load and requires scaling to a larger instance class for improved performance.


## Use Case 2: Identifying Inefficient Queries or Workloads <a name="example-2"></a>
Spikes in CPU usage may indicate inefficient query patterns, sudden workload surges, or unoptimized application behavior. This metric helps identify when tuning or indexing is required.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS DocumentDB CPU Utilization Metric Documentation
https://docs.aws.amazon.com/documentdb/latest/developerguide/cloud_watch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html