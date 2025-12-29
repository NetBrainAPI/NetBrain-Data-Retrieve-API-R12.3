# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Invalid Client Requests](#example-1) 
    - [Use Case 2 -- Monitoring Access Control and Throttling Errors](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>API Gateway 4XX Error Rate</b> metric tracks the total number of client-side HTTP 4XX errors returned by Amazon API Gateway. These errors occur when clients send invalid or unauthorized requests, such as missing parameters, malformed payloads, expired/incorrect API keys, or insufficient permissions. Monitoring this metric helps ensure API reliability and supports troubleshooting of client-side issues.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: 4XXError
* <b>Namespace</b>: AWS/ApiGateway
* <b>Unit / Stat</b>: SampleCount
* <b>Display Name in NetBrain</b>: 4XX Error Rate

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for analysis, helpful for both historical and real-time monitoring.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Count.
  * <b>Average</b>: Useful for spotting long-term trends in client error rates.
  * <b>Sum</b>: Shows the total number of client-side errors within the selected period.
  * <b>Minimum</b>: Identifies periods with no client errors.
  * <b>Maximum</b>: Highlights peak error bursts, helpful for identifying abnormal traffic patterns.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>60 seconds</b> for real-time troubleshooting.
    * <b>300 seconds</b> for operational monitoring.
    * <b>3600 seconds</b> for long-term trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Invalid Client Requests <a name="example-1"></a>
Use the <b>4XXError</b> metric to detect malformed requests, missing parameters, authentication failures, or calls to invalid endpoints. Monitoring helps pinpoint integration issues on the client side.

## Use Case 2: Monitoring Access Control and Throttling Errors <a name="example-2"></a>
A high rate of 401, 403, or 429 errors may indicate misconfigured IAM policies, incorrect API keys, or traffic exceeding throttle limits. This metric helps validate access policies and ensure correct API behavior.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS APIGateway Data In Metric Documentation
https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-metrics-and-dimensions.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html