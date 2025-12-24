# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Tracking Scaling-In Events](#example-1) 
    - [Use Case 2 -- Detecting Potential Issues with Instance Stability](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Terminating Instances</b> metric tracks the number of instances that are currently in the process of shutting down within an Auto Scaling group. This metric helps you understand when scaling-in actions occur, verify termination behavior, and detect any unexpected or rapid instance turnover.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: GroupTerminatingInstances
* <b>Namespace</b>: AWS/AutoScaling
* <b>Unit / Stat</b>: Maximum
* <b>Dimension</b>: AutoScalingGroupName
* <b>Display Name in NetBrain</b>: Terminating Instances

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period for monitoring instance terminations. Useful for understanding scaling-in patterns, identifying unexpected shutdown spikes, and validating lifecycle hook behavior.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Maximum.
  * <b>Maximum</b>: Shows the highest number of instances that entered the terminating state during the selected interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time termination event tracking.
    * <b>3600 seconds</b> for standard hourly lifecycle monitoring.
    * <b>7200 seconds</b> for long-term analysis of scale-in behavior.

# Use Cases Example <a name="example"></a>
## Use Case 1: Tracking Scaling-In Events <a name="example-1"></a>
Monitoring <b>GroupTerminatingInstances</b> helps identify when the Auto Scaling group is reducing capacity, validating whether scale-in policies are working as intended.
## Use Case 2: Detecting Potential Issues with Instance Stability <a name="example-2"></a>
Frequent or unexpected instance terminations may signal configuration problems, health check failures, or unstable workloads. This metric helps pinpoint such issues.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Auto Scaling Metrics Documentation
https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html