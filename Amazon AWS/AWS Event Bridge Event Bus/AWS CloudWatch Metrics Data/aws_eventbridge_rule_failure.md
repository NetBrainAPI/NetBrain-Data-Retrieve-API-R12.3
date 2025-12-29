# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Target Service Outages](#example-1) 
    - [Use Case 2 -- Troubleshooting Misconfigured Event Rules](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>EventBridge Rule Failures</b> metric tracks the number of failed invocations for EventBridge rules on an event bus. Invocation failures may occur due to misconfigured targets, permission issues, unreachable services, or malformed events. Monitoring this metric is essential for ensuring event routing reliability and detecting issues in event-driven architectures.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: FailedInvocations
* <b>Namespace</b>: AWS/Events
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: RuleName
* <b>Display Name in NetBrain</b>: Rule Failures

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used to analyze failed rule invocation attempts. Useful for identifying patterns and diagnosing disruptions in event delivery.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Indicates the number of failed invocation attempts during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed analysis of rule-level failures.
    * <b>3600 seconds</b> for standard hourly monitoring.
    * <b>7200 seconds</b> for long-range system reliability assessment.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Target Service Outages <a name="example-1"></a>
Rule invocation failures often occur when downstream services (Lambda, Step Functions, API endpoints, etc.) are unavailable or misconfigured. Monitoring <b>FailedInvocations</b> helps identify affected targets quickly.

## Use Case 2: Troubleshooting Misconfigured Event Rules <a name="example-2"></a>
Increases in rule failures may indicate permission issues, malformed events, or incorrect rule definitions. This metric helps isolate configuration errors impacting event flow.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS EventBridge Rule Metrics Documentation
https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-monitoring.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html