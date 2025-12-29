# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Preventing Storage Saturation](#example-1) 
    - [Use Case 2 -- Detecting Application or Message Flow Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Storage Utilization</b> metric measures the percentage of the allocated message store capacity currently used by an AmazonMQ broker. When storage usage approaches capacity limits, message persistence, throughput, and broker performance may be impacted. Monitoring this metric ensures appropriate storage planning and prevents disruptions in message processing.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: StorePercentUsage
* <b>Namespace</b>: AWS/AmazonMQ
* <b>Unit / Stat</b>: Percent
* <b>Dimension</b>: Broker
* <b>Display Name in NetBrain</b>: Storage Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window used to analyze message store usage. Useful for tracking storage growth trends, detecting spikes, and planning storage expansion.
* <b>Statistics</b>: Default value is Percent.
  * <b>Percent</b>: Indicates the percentage of the broker's message store that is currently in use.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed monitoring during high message ingestion.
    * <b>3600 seconds</b> for hourly storage usage visibility.
    * <b>7200 seconds</b> for long-range storage planning.

# Use Cases Example <a name="example"></a>
## Use Case 1: Preventing Storage Saturation <a name="example-1"></a>
Monitoring <b>StorePercentUsage</b> helps identify when message storage is approaching its limit, allowing for timely cleanups, retention adjustments, or storage upgrades.

## Use Case 2: Detecting Application or Message Flow Issues <a name="example-2"></a>
Rapid spikes in storage utilization may indicate message processing delays, unacknowledged messages, or consumer-side problems. This metric assists in diagnosing such issues early.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS AmazonMQ Metrics Documentation
https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html