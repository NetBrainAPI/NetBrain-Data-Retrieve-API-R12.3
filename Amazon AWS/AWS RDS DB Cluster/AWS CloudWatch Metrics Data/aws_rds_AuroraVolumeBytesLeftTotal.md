# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Preventing Storage Exhaustion](#example-1) 
    - [Use Case 2 -- Capacity Planning and Scaling Decisions](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Volume Bytes Left Total</b> metric reports the minimum available storage space, in bytes, remaining in an Amazon Aurora cluster volume. Monitoring this metric is essential for ensuring that your Aurora DB cluster has sufficient free space to store new data, maintain performance, and avoid storage-related outages.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: AuroraVolumeBytesLeftTotal
* <b>Namespace</b>: AWS/RDS
* <b>Unit / Stat</b>: Minimum
* <b>Dimension</b>: DBClusterIdentifier
* <b>Display Name in NetBrain</b>: Volume Bytes Left Total

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for analyzing available storage capacity. Helps identify storage trends, detect low-space thresholds, and plan for scaling or cleanup.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Minimum.
  * <b>Minimum</b>: Shows the lowest amount of free storage available during the selected time window.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed free-space monitoring.
    * <b>3600 seconds</b> for hourly storage trend visibility.
    * <b>7200 seconds</b> for long-term capacity planning.

# Use Cases Example <a name="example"></a>
## Use Case 1: Preventing Storage Exhaustion <a name="example-1"></a>
Monitoring <b>AuroraVolumeBytesLeftTotal</b> helps ensure that the Aurora cluster volume does not run out of space, which could lead to write failures or degraded performance.


## Use Case 2: Capacity Planning and Scaling Decisions <a name="example-2"></a>
Tracking trends in free storage supports forecasting when to scale the cluster, archive historical data, or optimize database schema and indexes.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS RDS and Aurora Storage Metrics Documentation
https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html