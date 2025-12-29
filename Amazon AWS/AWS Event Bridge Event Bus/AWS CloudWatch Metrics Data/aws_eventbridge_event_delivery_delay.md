# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Latency in Event Processing Pipelines](#example-1) 
    - [Use Case 2 -- Identifying System Performance Degradation](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Event Delivery Delay</b> metric measures the time taken for events to be successfully delivered from the EventBridge event bus to their configured targets. This metric helps identify latency in event processing pipelines, potential bottlenecks in downstream services, or delays caused by transient AWS infrastructure issues.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: IngestionToInvocationSuccessLatency
* <b>Namespace</b>: AWS/Events
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: RuleName
* <b>Display Name in NetBrain</b>: Event Delivery Delay

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window to analyze event delivery delays. Helps identify periods where event-to-target latency increased.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total number of latency measurements collected for successful event deliveries.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed latency monitoring.
    * <b>3600 seconds</b> for standard hourly analysis.
    * <b>7200 seconds</b> for long-term delivery performance trends.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Latency in Event Processing Pipelines <a name="example-1"></a>
Monitoring <b>IngestionToInvocationSuccessLatency</b> helps reveal delays caused by slow downstream targets, bursty event loads, or network latency.


## Use Case 2: Identifying System Performance Degradation <a name="example-2"></a>
Increased delivery delay may indicate AWS service throttling, target endpoint slowdowns, or event bus congestion. This metric aids in diagnosing and responding to these issues.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS EventBridge Latency Metrics Documentation
https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-monitoring.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html