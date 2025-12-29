# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Preventing Cache Exhaustion](#example-1) 
    - [Use Case 2 -- Optimizing Data Access Patterns](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Cache Disk Utilization</b> metric measures how much of the local cache disk on an AWS Storage Gateway appliance is being used. The cache helps optimize data retrieval and reduce latency for frequently accessed data. Monitoring this metric is essential for ensuring adequate cache capacity, preventing performance issues, and supporting efficient storage operations.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CacheUsed
* <b>Namespace</b>: AWS/StorageGateway
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: GatewayId
* <b>Display Name in NetBrain</b>: Cache Disk Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for analyzing cache usage trends. Useful for identifying peak usage periods, capacity bottlenecks, or changes in access patterns.
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total cache space consumed during the selected evaluation window.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed cache utilization analysis.
    * <b>3600 seconds</b> for standard hourly monitoring.
    * <b>7200 seconds</b> for long-term storage efficiency evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Preventing Cache Exhaustion <a name="example-1"></a>
Monitoring <b>CacheUsed</b> helps detect when cache space is approaching full utilization, enabling proactive scaling or cleanup actions to maintain peak performance.


## Use Case 2: Optimizing Data Access Patterns <a name="example-2"></a>
Higher-than-expected cache usage may indicate workload shifts, configuration tuning needs, or frequent access to large datasets. Tracking this metric assists in optimizing data flow and cache performance.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Storage Gateway Metrics Documentation
https://docs.aws.amazon.com/storagegateway/latest/userguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html