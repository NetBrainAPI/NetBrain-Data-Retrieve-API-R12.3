# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Broker Load and Performance](#example-1) 
    - [Use Case 2 -- Identifying Performance Bottlenecks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>CPU Utilization</b> metric measures the percentage of allocated CPU currently used by an AmazonMQ broker node. Monitoring this metric is essential for assessing broker performance, detecting workload spikes, ensuring message throughput stability, and determining when scaling or tuning is required.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CpuUtilization
* <b>Namespace</b>: AWS/AmazonMQ
* <b>Unit / Stat</b>: Percent
* <b>Dimension</b>: Broker
* <b>Display Name in NetBrain</b>: CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window used to monitor CPU usage trends. Helps identify periods of high processing demand or potential resource saturation.
* <b>Statistics</b>: Default value is Percent.
  * <b>Percent</b>: Represents the percentage of CPU utilized during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed CPU analysis during bursts.
    * <b>3600 seconds</b> for hourly CPU consumption tracking.
    * <b>7200 seconds</b> for long-term broker performance assessment.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Broker Load and Performance <a name="example-1"></a>
Tracking <b>CpuUtilization</b> helps determine when broker nodes are under heavy load, enabling proactive scaling or configuration adjustments to maintain stable messaging performance.


## Use Case 2: Identifying Performance Bottlenecks <a name="example-2"></a>
Sudden CPU spikes may indicate inefficient message consumers, high connection loads, or improperly tuned queues. This metric supports identifying and resolving such bottlenecks.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS AmazonMQ Metrics Documentation
https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html