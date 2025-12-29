# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Validating Cache Provisioning](#example-1) 
    - [Use Case 2 -- Detecting Configuration Changes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Cache Size</b> metric measures the total provisioned local cache capacity available on an AWS Storage Gateway appliance. This cache is used to store frequently accessed data locally, improving performance and reducing latency. Monitoring this metric helps validate cache provisioning and ensures that adequate storage capacity is allocated for expected workloads.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: TotalCacheSize
* <b>Namespace</b>: AWS/StorageGateway
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: GatewayId
* <b>Display Name in NetBrain</b>: Cache Size

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used to analyze total cache capacity. Useful for confirming whether the cache configuration remains consistent or has been adjusted over time.
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total provisioned cache capacity measured at each evaluation interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed cache provisioning validation.
    * <b>3600 seconds</b> for standard hourly visibility.
    * <b>7200 seconds</b> for long-term configuration tracking.

# Use Cases Example <a name="example"></a>
## Use Case 1: Validating Cache Provisioning <a name="example-1"></a>
Monitoring <b>TotalCacheSize</b> ensures that the Storage Gateway appliance is provisioned with sufficient cache capacity to support performance requirements and storage workloads.


## Use Case 2: Detecting Configuration Changes <a name="example-2"></a>
Sudden changes in total cache size may indicate configuration adjustments, storage expansions, or hardware modifications. Tracking this metric helps administrators maintain consistent configurations.
# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Storage Gateway Metrics Documentation
https://docs.aws.amazon.com/storagegateway/latest/userguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html