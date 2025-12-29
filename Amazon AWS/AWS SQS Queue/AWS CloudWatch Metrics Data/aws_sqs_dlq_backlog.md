# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Application Processing Failures](#example-1) 
    - [Use Case 2 -- Ensuring DLQ Does Not Overflow](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Messages Visible (DLQ Backlog)</b> metric represents the number of messages currently available for retrieval in an Amazon SQS Dead-Letter Queue (DLQ). A rising number of visible messages in the DLQ indicates that message processing failures are occurring in the primary queue. Monitoring this metric is essential for identifying application errors, retry exhaustion, and message-flow disruptions.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: ApproximateNumberOfMessagesVisible
* <b>Namespace</b>: AWS/SQS
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: QueueName
* <b>Display Name in NetBrain</b>: Messages Visible

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing DLQ backlog trends. Useful for identifying application failures or increasing message processing errors.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the latest approximate count of messages available in the DLQ during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time monitoring of DLQ growth.
    * <b>3600 seconds</b> for hourly backlog trend tracking.
    * <b>7200 seconds</b> for long-term analysis of message failure patterns.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Application Processing Failures <a name="example-1"></a>
A growing <b>ApproximateNumberOfMessagesVisible</b> value indicates message processing failures in the primary queue, helping identify issues such as malformed messages, unhandled exceptions, or application downtime.

## Use Case 2: Ensuring DLQ Does Not Overflow <a name="example-2"></a>
Monitoring DLQ backlog helps ensure that failed messages are addressed promptly, preventing long-term buildup and supporting timely debugging and recovery.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS SQS Queue Metrics Documentation
https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html