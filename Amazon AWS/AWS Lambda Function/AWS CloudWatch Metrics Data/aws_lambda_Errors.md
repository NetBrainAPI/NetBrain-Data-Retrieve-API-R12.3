# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Diagnosing Application or Code Errors](#example-1) 
    - [Use Case 2 -- Monitoring Deployment Stability](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Errors</b> metric tracks the number of AWS Lambda invocations that failed due to function errors, unhandled exceptions, timeouts, configuration problems, or internal Lambda service issues. Monitoring this metric is essential for maintaining application reliability, identifying faulty code paths, and ensuring proper exception handling.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: Errors
* <b>Namespace</b>: AWS/Lambda
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: FunctionName
* <b>Display Name in NetBrain</b>: Invocation Errors

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the timeframe for analyzing Lambda invocation failures. Useful for troubleshooting code defects, deployment issues, or dependency failures.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total count of failed invocations within the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time error detection.
    * <b>3600 seconds</b> for hourly reliability monitoring.
    * <b>7200 seconds</b> for long-term error pattern analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Diagnosing Application or Code Errors <a name="example-1"></a>
An increase in <b>Errors</b> may indicate bugs, unhandled exceptions, invalid input, or dependency failures in your Lambda function logic.



## Use Case 2: Monitoring Deployment Stability <a name="example-2"></a>
Error spikes immediately after new deployments often reveal regressions or configuration mistakes. This metric helps validate function behavior post-deployment.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Lambda Metrics Documentation
https://docs.aws.amazon.com/lambda/latest/dg/monitoring-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html