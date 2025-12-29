# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Concurrency Limit Bottlenecks](#example-1) 
    - [Use Case 2 -- Capacity Planning for High-Traffic Applications](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Throttles</b> metric counts the number of AWS Lambda invocation requests that were throttled because they exceeded the configured concurrency limits. Throttling occurs when the function’s reserved concurrency or the account-level concurrency pool is fully consumed. Monitoring this metric helps ensure adequate concurrency provisioning and prevents service slowdowns.




# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: Throttles
* <b>Namespace</b>: AWS/Lambda
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: FunctionName
* <b>Display Name in NetBrain</b>: Invocation Throttles

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for tracking throttled invocation attempts. Useful for identifying concurrency shortages, sudden traffic spikes, or misconfigured scaling behaviors.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total number of throttled invocation requests during the selected time range.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time concurrency saturation tracking.
    * <b>3600 seconds</b> for hourly monitoring of invocation health.
    * <b>7200 seconds</b> for long-term concurrency planning and optimization.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Concurrency Limit Bottlenecks <a name="example-1"></a>
A rise in <b>Throttles</b> indicates that your Lambda function is hitting concurrency limits, potentially causing delays or failures in your application workflow.

## Use Case 2: Capacity Planning for High-Traffic Applications <a name="example-2"></a>
Monitoring throttles helps ensure concurrency settings and scaling policies meet real-world traffic demands, especially for bursty or unpredictable workloads.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Lambda Metrics Documentation
https://docs.aws.amazon.com/lambda/latest/dg/monitoring-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html