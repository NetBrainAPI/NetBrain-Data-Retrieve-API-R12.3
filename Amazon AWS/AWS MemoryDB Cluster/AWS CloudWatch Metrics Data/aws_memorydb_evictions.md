# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying AWS-Side Service Issues](#example-1) 
    - [Use Case 2 -- Optimizing Data Storage and Cache Behavior](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Key Evictions</b> metric tracks the number of keys removed from an AWS MemoryDB cluster due to memory pressure. Evictions typically occur when the dataset grows beyond the available memory and the system is forced to free space by removing less recently used keys. Monitoring this metric helps identify memory constraints and ensure that the database is configured to handle the workload efficiently.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: Evictions
* <b>Namespace</b>: AWS/MemoryDB
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: ClusterName
* <b>Display Name in NetBrain</b>: Key Evictions

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the timeframe for analyzing eviction activity. Useful for detecting periods of high memory demand or inefficient memory usage patterns.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the number of key eviction events during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed eviction monitoring.
    * <b>3600 seconds</b> for hourly trend analysis.
    * <b>7200 seconds</b> for long-term memory pressure assessment.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying AWS-Side Service Issues <a name="example-1"></a>
Frequent <b>Evictions</b> indicate that the MemoryDB cluster is running out of available memory. This helps determine whether scaling up or modifying data structures is required.



## Use Case 2: Optimizing Data Storage and Cache Behavior <a name="example-2"></a>
Elevated eviction counts may indicate that TTL policies, caching strategies, or dataset sizes need optimization to prevent unintended data loss.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS MemoryDB Metrics Documentation
https://docs.aws.amazon.com/memorydb/latest/devguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html