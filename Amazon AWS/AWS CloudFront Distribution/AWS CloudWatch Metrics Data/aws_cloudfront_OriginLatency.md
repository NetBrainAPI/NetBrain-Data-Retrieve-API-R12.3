# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Origin Performance Bottlenecks](#example-1) 
    - [Use Case 2 -- Monitoring Network Issues Between CloudFront and Origin](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Origin Latency</b> metric measures the amount of time, in milliseconds, between when CloudFront receives a viewer request and when it begins returning a response from the origin. This includes network latency, processing time at the origin, and any intermediate transfer delays. Monitoring this metric helps detect backend performance issues, optimize origin configurations, and ensure responsive delivery of content.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: OriginLatency
* <b>Namespace</b>: AWS/CloudFront
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DistributionId
* <b>Display Name in NetBrain</b>: Origin Latency

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Specifies the time window used to analyze origin response times. Useful for identifying backend latency spikes, overloaded origins, or network degradation.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean time (in milliseconds) taken for CloudFront to receive the first byte from the origin.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed latency troubleshooting.
    * <b>3600 seconds</b> for hourly backend performance monitoring.
    * <b>7200 seconds</b> for long-term latency trend tracking.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Origin Performance Bottlenecks <a name="example-1"></a>
A rise in <b>OriginLatency</b> may indicate slow processing at the origin server, heavy load, inefficient database queries, or content generation delays.


## Use Case 2: Monitoring Network Issues Between CloudFront and Origin <a name="example-2"></a>
Increased latency may also stem from cross-region network delays or connectivity issues. Tracking this metric helps diagnose and resolve such problems quickly.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS CloudFront Metrics Documentation
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/monitoring-using-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html