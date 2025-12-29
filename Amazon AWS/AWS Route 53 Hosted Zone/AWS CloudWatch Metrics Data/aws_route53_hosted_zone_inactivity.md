# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Inactive Hosted Zones](#example-1) 
    - [Use Case 2 -- Troubleshooting DNS Misconfigurations](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Hosted Zone Inactivity</b> metric tracks the number of DNS queries received by a Route 53 hosted zone. Monitoring this metric helps identify whether a hosted zone is actively serving traffic or has become inactive. A lack of DNS queries may indicate misconfigurations, unused zones, or potential issues in domain routing.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: DNSQueries
* <b>Namespace</b>: AWS/Route53
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: HostedZoneId
* <b>Display Name in NetBrain</b>: DNS Query Inactivity

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing DNS query volume for the hosted zone. Useful for identifying inactive zones or validating traffic-related behavior.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the number of DNS queries recorded during each interval.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed real-time query monitoring.
    * <b>3600 seconds</b> for standard hourly inactivity detection.
    * <b>7200 seconds</b> for long-term DNS traffic evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Inactive Hosted Zones <a name="example-1"></a>
Monitoring <b>DNSQueries</b> helps identify zones receiving zero or minimal traffic, useful when reviewing unused domains, stale test environments, or incorrectly routed DNS records.


## Use Case 2: Troubleshooting DNS Misconfigurations <a name="example-2"></a>
A sudden drop in DNS query counts may indicate issues such as incorrect name server delegation, expired domains, or routing configuration errors. This metric assists in diagnosing traffic flow disruptions.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Route 53 DNS Query Metrics Documentation
https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html
