# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Delayed Launches](#example-1) 
    - [Use Case 2 -- Validating Scaling-Out Behavior](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Pending Instances</b> metric measures the number of instances in an Auto Scaling group that are in the launching phase but not yet available for use. This includes instances that are initializing, undergoing health checks, or installing required configurations. Monitoring this metric helps ensure scaling activities proceed as expected and identifies delays in the instance launch lifecycle.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: GroupPendingInstances
* <b>Namespace</b>: AWS/AutoScaling
* <b>Unit / Stat</b>: Maximum
* <b>Dimension</b>: AutoScalingGroupName
* <b>Display Name in NetBrain</b>: Pending Instances

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Specifies the time range for monitoring instances in the pending state. Useful for identifying slow launches, capacity issues, or scaling delays.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Maximum.
  * <b>Maximum</b>: Shows the highest number of pending instances during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed launch-phase diagnostics.
    * <b>3600 seconds</b> for hourly scaling behavior monitoring.
    * <b>7200 seconds</b> for long-term reliability assessment of the launch process.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Delayed Launches <a name="example-1"></a>
A high count of <b>GroupPendingInstances</b> may suggest problems with AMIs, launch configurations, instance warm-up, or insufficient capacity in the target Availability Zone.
## Use Case 2: Validating Scaling-Out Behavior <a name="example-2"></a>
Monitoring pending instances helps ensure scaling policies successfully launch new instances during traffic surges or scheduled scale-out events.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Auto Scaling Metrics Documentation
https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html