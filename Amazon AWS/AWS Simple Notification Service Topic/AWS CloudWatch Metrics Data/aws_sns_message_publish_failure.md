# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Endpoint or Subscriber Failures](#example-1) 
    - [Use Case 2 -- Monitoring SNS Delivery Reliability](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Message Publish Failures</b> metric measures the number of messages that Amazon SNS failed to deliver to its subscribers. Failures may occur due to endpoint issues, permission problems, throttling, misconfigurations, or temporary service disruptions. Monitoring this metric is critical for ensuring message delivery reliability and diagnosing issues within event-driven or notification-based applications.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: NumberOfNotificationsFailed
* <b>Namespace</b>: AWS/SNS
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: TopicName
* <b>Display Name in NetBrain</b>: Message Publish Failures

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for evaluating failed notification attempts. Useful for identifying delivery issues and correlating them with endpoint or application outages.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total number of failed notification attempts during each evaluation interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed failure analysis and rapid issue detection.
    * <b>3600 seconds</b> for hourly monitoring of delivery reliability.
    * <b>7200 seconds</b> for long-term trend evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Endpoint or Subscriber Failures <a name="example-1"></a>
Spikes in <b>NumberOfNotificationsFailed</b> may indicate subscriber endpoint outages, permission issues, or unreachable services. This helps identify and troubleshoot downstream integration issues.

## Use Case 2: Monitoring SNS Delivery Reliability <a name="example-2"></a>
Tracking failures helps confirm whether SNS is meeting the application’s reliability requirements and can reveal throttling, misconfigurations, or malformed messages.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS SNS Delivery and Failure Metrics Documentation
https://docs.aws.amazon.com/sns/latest/dg/sns-monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html