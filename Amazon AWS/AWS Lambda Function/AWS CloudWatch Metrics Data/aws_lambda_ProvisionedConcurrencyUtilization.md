# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Ensuring Provisioned Concurrency Is Adequately Utilized](#example-1) 
    - [Use Case 2 -- Preventing Cold Starts During Peak Traffic](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Provisioned Concurrency Utilization</b> metric measures the percentage of provisioned concurrency currently being used by an AWS Lambda function to serve incoming requests. This metric helps ensure that your function has sufficient pre-initialized execution environments to avoid cold starts, maintain low latency, and handle expected traffic patterns efficiently.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: Provisioned Concurrency Utilization
* <b>Namespace</b>: AWS/Lambda
* <b>Unit / Stat</b>: Maximum
* <b>Dimension</b>: FunctionName
* <b>Display Name in NetBrain</b>: Provisioned Concurrency Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Specifies the time range for analyzing how much of the allocated provisioned concurrency is actively in use. Useful for optimizing configuration and ensuring adequate capacity.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Maximum.
  * <b>Maximum</b>: Indicates the highest percentage of provisioned concurrency consumed during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed visibility into utilization fluctuations.
    * <b>3600 seconds</b> for hourly performance monitoring.
    * <b>7200 seconds</b> for long-term concurrency planning.

# Use Cases Example <a name="example"></a>
## Use Case 1: Ensuring Provisioned Concurrency Is Adequately Utilized <a name="example-1"></a>
Monitoring this metric helps determine whether you have under- or over-provisioned concurrency, aiding in cost and performance optimization.


## Use Case 2: Preventing Cold Starts During Peak Traffic <a name="example-2"></a>
High utilization may indicate the need to increase provisioned concurrency to ensure the function continues to avoid cold starts during traffic bursts.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Lambda Metrics Documentation
https://docs.aws.amazon.com/lambda/latest/dg/monitoring-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html