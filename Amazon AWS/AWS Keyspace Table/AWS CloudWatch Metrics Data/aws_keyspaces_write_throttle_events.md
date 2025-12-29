# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Ensuring Adequate Write Capacity](#example-1) 
    - [Use Case 2 -- Improving Write Performance and Reducing Latency](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Write Throttling Events</b> metric tracks the number of throttled write operations for Amazon Keyspaces (for Apache Cassandra) tables. Throttling occurs when write requests exceed the provisioned write capacity or when burst capacity is insufficient. Monitoring this metric is essential for maintaining application performance, preventing write delays, and ensuring that the table is configured with appropriate throughput.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: WriteThrottleEvents
* <b>Namespace</b>: AWS/Keyspaces
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: TableName
* <b>Display Name in NetBrain</b>: Write Throttling Events

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Sets the time period used to analyze write throttling activity. Helps identify peak write load periods or insufficient write capacity provisioning.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total number of write operations that were throttled during the selected time window.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed write throttling diagnostics.
    * <b>3600 seconds</b> for hourly operational visibility.
    * <b>7200 seconds</b> for long-term capacity planning trends.

# Use Cases Example <a name="example"></a>
## Use Case 1: Ensuring Adequate Write Capacity <a name="example-1"></a>
Monitoring <b>WriteThrottleEvents</b> helps determine when a Keyspaces table is hitting its write capacity limits and may need auto-scaling adjustments or higher provisioned throughput.

## Use Case 2: Improving Write Performance and Reducing Latency <a name="example-2"></a>
Write throttling can lead to delays or failed write attempts in applications. Tracking this metric helps diagnose performance bottlenecks and optimize Keyspaces throughput configurations.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Keyspaces Metrics Documentation
https://docs.aws.amazon.com/keyspaces/latest/devguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html