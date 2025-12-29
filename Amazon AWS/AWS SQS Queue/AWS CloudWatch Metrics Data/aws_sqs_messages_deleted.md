# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Message Processing Throughput](#example-1) 
    - [Use Case 2 -- Detecting Processing Failures or Consumer Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Messages Deleted</b> metric tracks the number of messages successfully removed from an Amazon SQS queue using the <i>DeleteMessage</i> or <i>DeleteMessageBatch</i> API calls. This metric reflects the rate at which consumers are finishing message processing and helps ensure that queue workloads are being handled efficiently.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: NumberOfMessagesDeleted
* <b>Namespace</b>: AWS/SQS
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: QueueName
* <b>Display Name in NetBrain</b>: Messages Deleted

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for analyzing message deletion behavior. Useful for monitoring processing throughput, identifying stalled consumers, or validating queue processing logic.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total number of messages deleted from the queue during the specified period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed analysis of consumer throughput.
    * <b>3600 seconds</b> for hourly trend monitoring.
    * <b>7200 seconds</b> for long-term processing pattern evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Message Processing Throughput <a name="example-1"></a>
Tracking <b>NumberOfMessagesDeleted</b> helps confirm that consumers are completing message processing and successfully deleting messages from the queue.


## Use Case 2: Detecting Processing Failures or Consumer Issues <a name="example-2"></a>
A sudden decrease in message deletions may indicate consumer failures, long processing times, or configuration issues. This metric aids in early detection of such problems.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS SQS Queue Metrics Documentation
https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html