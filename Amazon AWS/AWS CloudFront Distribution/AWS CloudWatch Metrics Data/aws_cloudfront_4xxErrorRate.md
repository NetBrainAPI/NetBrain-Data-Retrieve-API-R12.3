# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Client-Side Issues or Resource Errors](#example-1) 
    - [Use Case 2 -- Validating Application Changes and Deployments](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>4xx Error Rate</b> metric measures the percentage of viewer requests to an Amazon CloudFront distribution that return HTTP 4xx status codes. These errors typically indicate client-side issues such as invalid requests, missing resources, or unauthorized access. Monitoring this metric helps identify misconfigurations, broken links, authentication failures, or unexpected client behavior.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: 4xxErrorRate
* <b>Namespace</b>: AWS/CloudFront
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DistributionId
* <b>Display Name in NetBrain</b>: 4xx Error Rate

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Specifies the time range for monitoring 4xx error percentages. Useful for identifying spikes in client-side issues, deployments that introduce faults, or unexpected request patterns.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Shows the mean percentage of viewer requests that returned 4xx errors during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed detection of sudden client error spikes.
    * <b>3600 seconds</b> for hourly trend monitoring.
    * <b>7200 seconds</b> for long-term performance and traffic quality assessment.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Client-Side Issues or Resource Errors <a name="example-1"></a>
A rise in the <b>4xxErrorRate</b> metric may signal missing resources (404), unauthorized access attempts (401/403), or malformed client requests.



## Use Case 2: Validating Application Changes and Deployments <a name="example-2"></a>
If 4xx errors increase after a deployment, it may indicate broken URLs, removed content, or misconfigured origin permissions. This metric helps quickly identify such issues.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS CloudFront Metrics Documentation
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html