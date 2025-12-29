# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Memory Pressure and Scaling Needs](#example-1) 
    - [Use Case 2 -- Identifying Inefficient Workloads or Data Growth](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Memory Usage</b> metric measures the percentage of memory consumed by an AWS MemoryDB cluster. Since MemoryDB is an in-memory database, monitoring memory utilization is essential to ensure optimal performance, avoid out-of-memory conditions, and support decisions around scaling or workload distribution.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: DatabaseMemoryUsagePercentage
* <b>Namespace</b>: AWS/MemoryDB
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: ClusterName
* <b>Display Name in NetBrain</b>: Memory Usage

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window to analyze memory usage patterns of the MemoryDB cluster. Useful for detecting memory pressure, workload spikes, or sustained high utilization.
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Indicates the mean memory consumption percentage over the selected time period
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for granular performance monitoring.
    * <b>3600 seconds</b> for standard hourly memory trend analysis.
    * <b>7200 seconds</b> for long-term memory usage forecasting.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Memory Pressure and Scaling Needs <a name="example-1"></a>
High <b>DatabaseMemoryUsagePercentage</b> values indicate increasing storage demand or inefficient data structures. Monitoring helps determine when cluster scaling or memory optimization is needed.


## Use Case 2: Identifying Inefficient Workloads or Data Growth <a name="example-2"></a>
Sudden memory spikes may indicate inefficient caching patterns, increased data ingestion, or unoptimized application logic. This metric supports root-cause analysis.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS MemoryDB Metrics Documentation
https://docs.aws.amazon.com/memorydb/latest/devguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html