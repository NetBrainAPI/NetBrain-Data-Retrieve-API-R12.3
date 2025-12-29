# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting High Event Volume Bursts](#example-1) 
    - [Use Case 2 -- Troubleshooting Downstream Service Bottlenecks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Rule Throttles</b> metric measures how many times EventBridge rule executions were throttled due to exceeding permitted invocation rates on the event bus. Throttling may occur during high event volumes or misconfigured rule targets. Monitoring this metric is essential for ensuring reliable event processing and identifying performance bottlenecks across event-driven systems.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: ThrottledRules
* <b>Namespace</b>: AWS/Events
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: RuleName
* <b>Display Name in NetBrain</b>: Rule Throttles

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the analysis window for determining when rule invocations were throttled. Helps correlate throttling occurrences with event bursts or downstream service slowdowns.
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the number of throttled rule executions recorded during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed throttling diagnostics.
    * <b>3600 seconds</b> for standard hourly performance tracking.
    * <b>7200 seconds</b> for long-term system health assessment.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting High Event Volume Bursts <a name="example-1"></a>
Monitoring <b>ThrottledRules</b> helps identify when the event bus is experiencing high invocation demand, causing temporary throttling of rule execution.


## Use Case 2: Troubleshooting Downstream Service Bottlenecks <a name="example-2"></a>
Rule throttling may occur if targets such as Lambda, Step Functions, or API endpoints are slow or overloaded. This metric helps pinpoint where processing delays originate.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS EventBridge Rule Metrics Documentation
https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-monitoring.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html