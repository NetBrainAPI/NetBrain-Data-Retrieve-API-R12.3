# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Backend or Origin Failures](#example-1) 
    - [Use Case 2 -- Monitoring Global Distribution Performance](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>5xx Error Rate</b> metric measures the percentage of viewer requests to a CloudFront distribution that result in HTTP 5xx responses. These server-side errors typically indicate backend failures, origin issues, misconfigurations, or capacity constraints. Monitoring this metric helps ensure service reliability, origin health, and optimal end-user experience.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: 5xxErrorRate
* <b>Namespace</b>: AWS/CloudFront
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DistributionId
* <b>Display Name in NetBrain</b>: 5xx Error Rate

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the timeframe for analyzing the proportion of server-side errors. Useful for detecting backend outages, origin misconfigurations, or global service degradations.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean percentage of viewer requests that experienced 5xx errors during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time server error detection.
    * <b>3600 seconds</b> for hourly monitoring.
    * <b>7200 seconds</b> for long-term trend analysis and origin performance evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Backend or Origin Failures <a name="example-1"></a>
Increases in <b>5xxErrorRate</b> can signal issues such as origin server downtime, connection timeouts, or misconfigured load balancers.



## Use Case 2: Monitoring Global Distribution Performance <a name="example-2"></a>
CloudFront distributes content across edge locations globally. A spike in server-side errors may indicate regional origin health issues, capacity limits, or misrouted traffic.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS CloudFront Metrics Documentation
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html