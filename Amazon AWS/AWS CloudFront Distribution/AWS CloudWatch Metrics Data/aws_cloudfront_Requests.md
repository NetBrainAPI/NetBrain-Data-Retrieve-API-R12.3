# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring CDN Traffic Volume](#example-1) 
    - [Use Case 2 -- Identifying Traffic Spikes or Anomalies](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Viewer Requests</b> metric tracks the total number of viewer requests received by an Amazon CloudFront distribution.
Monitoring this metric helps analyze traffic patterns, understand content popularity, and assess workload distribution across the CDN edge locations.
# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: Requests
* <b>Namespace</b>: AWS/CloudFront
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: DistributionId
* <b>Display Name in NetBrain</b>: Viewer Requests

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for evaluating viewer request counts. Useful for monitoring daily traffic volume, diagnosing sudden spikes, or performing trend analysis.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Shows the total number of viewer requests received within the specified evaluation period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for high-resolution traffic monitoring.
    * <b>3600 seconds</b> for hourly traffic insights.
    * <b>7200 seconds</b> for long-term activity analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring CDN Traffic Volume <a name="example-1"></a>
Tracking the <b>Requests</b> metric provides insight into user demand and helps optimize cache behavior or distribution scaling.


## Use Case 2: Identifying Traffic Spikes or Anomalies <a name="example-2"></a>
A sudden spike or drop in viewer requests can indicate marketing events, outages, configuration issues, or bot traffic.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS CloudFront Metrics Documentation
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/monitoring-cloudfront.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html