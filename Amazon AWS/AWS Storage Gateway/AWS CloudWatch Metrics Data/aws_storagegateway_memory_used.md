# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Resource Consumption Trends](#example-1) 
    - [Use Case 2 -- Diagnosing Performance Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Memory Utilization</b> metric measures the amount of memory currently used by an AWS Storage Gateway appliance. Monitoring memory utilization helps ensure the appliance has sufficient resources to process workloads, cache data, handle active transfers, and operate efficiently without performance degradation.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: MemUsedBytes
* <b>Namespace</b>: AWS/StorageGateway
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: GatewayId
* <b>Display Name in NetBrain</b>: Memory Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used to analyze memory consumption patterns. Useful for detecting memory pressure, spikes in usage, or performance concerns related to workload changes.
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total amount of memory used at each evaluation interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed memory utilization tracking.
    * <b>3600 seconds</b> for standard hourly monitoring.
    * <b>7200 seconds</b> for long-term memory demand analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Resource Consumption Trends <a name="example-1"></a>
Tracking <b>MemUsedBytes</b> helps determine whether memory usage is increasing over time, indicating possible workload growth or inefficiencies.


## Use Case 2: Diagnosing Performance Issues <a name="example-2"></a>
High memory utilization may degrade Storage Gateway performance or lead to slower data processing. This metric assists in identifying when additional resources or tuning is required.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Storage Gateway Metrics Documentation
https://docs.aws.amazon.com/storagegateway/latest/userguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html