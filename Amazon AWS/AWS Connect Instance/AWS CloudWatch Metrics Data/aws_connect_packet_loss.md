# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Audio Quality Degradation](#example-1) 
    - [Use Case 2 -- Identifying Network or Infrastructure Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>AWS Connect Instance Packet Loss</b> metric measures the percentage of packets lost during voice calls handled by an Amazon Connect instance. Packet loss directly affects call quality, resulting in audio distortion, delays, or dropped voice segments. Monitoring this metric is essential for ensuring stable network performance, maintaining call clarity, and identifying connectivity issues within the instance.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: ToInstancePacketLossRate
* <b>Namespace</b>: AWS/Connect
* <b>Unit / Stat</b>: Percent
* <b>Dimension</b>: InstanceId
* <b>Display Name in NetBrain</b>: Instance Packet Loss

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing packet loss trends. Helps identify periods of degraded audio quality.
* <b>Statistics</b>: Default value is Percent.
  * <b>Percent</b>: Shows the packet loss ratio for calls within the specified period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed monitoring and troubleshooting call quality issues.
    * <b>3600 seconds</b> for hourly performance visibility.
    * <b>7200 seconds</b> for long-term network quality trends.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Audio Quality Degradation <a name="example-1"></a>
Track the <b>ToInstancePacketLossRate</b> metric to detect periods where network instability or bandwidth limitations cause degraded audio quality during calls.

## Use Case 2: Identifying Network or Infrastructure Issues <a name="example-2"></a>
Elevated packet loss values may indicate WAN issues, ISP instability, VPN congestion, or misconfigured network devices. This metric helps isolate the root cause of voice quality problems.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Connect Packet Loss Metric Documentation
https://docs.aws.amazon.com/connect/latest/adminguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html