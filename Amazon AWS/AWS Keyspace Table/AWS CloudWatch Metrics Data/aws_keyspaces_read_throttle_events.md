# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Ensuring Adequate Read Capacity](#example-1) 
    - [Use Case 2 -- Troubleshooting Performance Bottlenecks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Read Throttling Events</b> metric measures the number of throttled read requests for Amazon Keyspaces (for Apache Cassandra) tables. Throttling occurs when read request rates exceed the configured read capacity or when burst capacity is exhausted. Monitoring this metric helps ensure consistent application performance and identify when capacity adjustments are required.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: ReadThrottleEvents
* <b>Namespace</b>: AWS/Keyspaces
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: TableName
* <b>Display Name in NetBrain</b>: Read Throttling Events

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing throttled read events. Helps identify high-load periods and potential capacity constraints.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the number of read operations that were throttled during the selected time range.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed throttling diagnostics and monitoring.
    * <b>3600 seconds</b> for standard hourly visibility.
    * <b>7200 seconds</b> for long-term capacity trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Ensuring Adequate Read Capacity <a name="example-1"></a>
Tracking <b>ReadThrottleEvents</b> helps identify when Keyspaces tables require increased read capacity or when table-level auto-scaling should be adjusted.

## Use Case 2: Troubleshooting Performance Bottlenecks <a name="example-2"></a>
Throttling can cause slow read response times or failed read operations. Monitoring this metric helps diagnose when throttling is affecting application behavior.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Keyspaces Metrics Documentation
https://docs.aws.amazon.com/keyspaces/latest/devguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html