# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Validating System Resource Configuration](#example-1) 
    - [Use Case 2 -- Detecting Hardware or Configuration Changes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Memory Size</b> metric measures the total memory available on an AWS Storage Gateway appliance. This metric is useful for confirming hardware capacity, validating configuration, and supporting monitoring of memory allocation against usage to ensure optimal system performance.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: MemTotalBytes
* <b>Namespace</b>: AWS/StorageGateway
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: GatewayId
* <b>Display Name in NetBrain</b>: Memory Size

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing the total available memory on the Storage Gateway appliance. Helps verify resource consistency or detect configuration changes over time.
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total memory capacity at each measurement interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed resource configuration tracking.
    * <b>3600 seconds</b> for standard hourly validation.
    * <b>7200 seconds</b> for long-term capacity monitoring.

# Use Cases Example <a name="example"></a>
## Use Case 1: Validating System Resource Configuration <a name="example-1"></a>
Monitoring <b>MemTotalBytes</b> ensures the Storage Gateway appliance has the expected memory capacity for its workload requirements.


## Use Case 2: Detecting Hardware or Configuration Changes <a name="example-2"></a>
Sudden shifts in total memory may indicate appliance configuration changes, updates, or hardware adjustments. This metric helps track and verify such changes.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Storage Gateway Metrics Documentation
https://docs.aws.amazon.com/storagegateway/latest/userguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html