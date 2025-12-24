# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Auto Scaling Group Health](#example-1) 
    - [Use Case 2 -- Detecting Failures or Scaling Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>In-Service DB Instances</b> metric tracks the number of instances in an Auto Scaling group that are currently healthy, active, and serving traffic. Monitoring this metric helps ensure that the Auto Scaling group maintains the desired capacity, supports workload demands, and continues to operate reliably even during scaling events or failures.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: GroupInServiceInstances
* <b>Namespace</b>: AWS/AutoScaling
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: AutoScalingGroupName
* <b>Display Name in NetBrain</b>: In-Service DB Instances

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing the number of active instances. Useful for understanding scaling behavior, detecting failures, and validating desired capacity.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean number of in-service instances during the selected time window.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed scaling activity analysis.
    * <b>3600 seconds</b> for hourly operational visibility.
    * <b>7200 seconds</b> for long-term scaling trend evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Auto Scaling Group Health <a name="example-1"></a>
Tracking <b>GroupInServiceInstances</b> helps ensure that the Auto Scaling group consistently maintains the necessary number of healthy instances to meet application demand.
## Use Case 2: Detecting Failures or Scaling Issues <a name="example-2"></a>
A drop in in-service instances may indicate instance failures, launch configuration problems, or insufficient capacity. This metric helps identify and resolve such issues quickly.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Auto Scaling Metrics Documentation
https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html

