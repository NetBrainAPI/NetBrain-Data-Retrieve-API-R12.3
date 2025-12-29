# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Consumer Activity](#example-1) 
    - [Use Case 2 -- Detecting Application or Consumption Slowdowns](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Messages Received</b> metric tracks the number of messages returned by the <i>ReceiveMessage</i> API for an Amazon SQS queue. Monitoring this metric helps verify message flow, detect consumption patterns, and ensure that consumers are actively polling the queue as expected.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: NumberOfMessagesReceived
* <b>Namespace</b>: AWS/SQS
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: QueueName
* <b>Display Name in NetBrain</b>: Messages Received

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for analyzing message retrieval activity. Useful for monitoring consumer behavior, identifying consumption gaps, or validating system throughput.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total count of messages retrieved from the queue during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time consumer activity monitoring.
    * <b>3600 seconds</b> for hourly message flow analysis.
    * <b>7200 seconds</b> for long-term workload pattern evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Consumer Activity <a name="example-1"></a>
Tracking <b>NumberOfMessagesReceived</b> helps confirm that consumers are actively polling the queue and processing messages as expected.


## Use Case 2: Detecting Application or Consumption Slowdowns <a name="example-2"></a>
A sudden drop in received messages may indicate consumer outages, processing delays, or configuration issues. This metric supports quick detection of such disruptions.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS SQS Queue Metrics Documentation
https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html