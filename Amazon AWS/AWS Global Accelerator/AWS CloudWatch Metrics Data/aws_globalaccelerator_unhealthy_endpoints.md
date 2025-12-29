# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Endpoint Failures](#example-1) 
    - [Use Case 2 -- Troubleshooting Infrastructure or Application Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Endpoint Health Status</b> metric measures the number of unhealthy endpoints associated with an AWS Global Accelerator. An endpoint may become unhealthy due to application issues, network failures, misconfigurations, or backend service degradation. Monitoring this metric helps ensure high availability and optimal traffic routing for global applications.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: UnhealthyEndpointCount
* <b>Namespace</b>: AWS/GlobalAccelerator
* <b>Unit / Stat</b>: Count
* <b>Dimension</b>: Accelerator
* <b>Display Name in NetBrain</b>: Endpoint Health Status

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used for analyzing endpoint health status. Useful for identifying when endpoint health degraded and correlating it with system events or traffic spikes.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Count.
  * <b>Count</b>: Represents the number of endpoints reported as unhealthy during each evaluation period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed health monitoring and faster detection of endpoint failures.
    * <b>3600 seconds</b> for standard hourly availability tracking..
    * <b>7200 seconds</b> for long-term endpoint health trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Endpoint Failures <a name="example-1"></a>
Monitoring <b>UnhealthyEndpointCount</b> helps identify when backend services become unavailable, allowing traffic to be routed away from unhealthy endpoints to maintain availability.


## Use Case 2: Troubleshooting Infrastructure or Application Issues <a name="example-2"></a>
Spikes in unhealthy endpoints may indicate network failures, misconfigured health checks, or degraded application performance. This metric supports root-cause analysis and rapid remediation.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Global Accelerator Endpoint Metrics Documentation
https://docs.aws.amazon.com/global-accelerator/latest/dg/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html