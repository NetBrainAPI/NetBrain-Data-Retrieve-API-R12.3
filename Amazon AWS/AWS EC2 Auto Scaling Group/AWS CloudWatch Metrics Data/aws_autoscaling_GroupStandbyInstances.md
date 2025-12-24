# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Maintenance Operations](#example-1) 
    - [Use Case 2 -- Detecting Configuration or Operational Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Standby Instances</b> metric measures the number of instances in an Auto Scaling group that are currently in standby mode. These instances are not serving traffic but remain part of the group, typically used for maintenance, troubleshooting, or planned operations without removing the instance from the group. Monitoring this metric helps ensure proper capacity planning and operational consistency.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: GroupStandbyInstances
* <b>Namespace</b>: AWS/AutoScaling
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: AutoScalingGroupName
* <b>Display Name in NetBrain</b>: Standby Instances

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period for analyzing the number of instances in standby state. Useful for understanding maintenance trends, confirming operational procedures, or detecting unexpected standby events.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean number of standby instances during the selected evaluation window.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed standby activity monitoring.
    * <b>3600 seconds</b> for hourly lifecycle visibility.
    * <b>7200 seconds</b> for long-term operational trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Maintenance Operations <a name="example-1"></a>
Tracking <b>GroupStandbyInstances</b> helps ensure that instances placed in standby for troubleshooting or updates do not inadvertently cause capacity shortages.
## Use Case 2: Detecting Configuration or Operational Issues <a name="example-2"></a>
Unexpected standby instances may signal misconfigurations, automation problems, or operational oversights. This metric supports early detection of such anomalies.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Auto Scaling Metrics Documentation
https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html