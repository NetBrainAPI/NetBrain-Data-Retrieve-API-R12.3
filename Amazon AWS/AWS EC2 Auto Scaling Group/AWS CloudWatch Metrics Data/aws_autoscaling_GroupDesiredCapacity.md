# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Validating Auto Scaling Policy Behavior](#example-1) 
    - [Use Case 2 -- Detecting Unintended Configuration Changes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Desired Capacity</b> metric tracks the number of instances that an Auto Scaling group is configured to maintain. This value reflects the expected instance count that the Auto Scaling group strives to keep active. Monitoring this metric helps validate scaling policies, ensure consistency in the desired state, and detect any unintended changes to configuration.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: GroupDesiredCapacity
* <b>Namespace</b>: AWS/AutoScaling
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: AutoScalingGroupName
* <b>Display Name in NetBrain</b>: Desired Capacity

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the analysis window for observing the desired capacity of the Auto Scaling group. Useful for understanding scaling policy adjustments and ensuring configuration accuracy.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Shows the mean desired capacity over the selected time period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed scaling policy behavior tracking.
    * <b>3600 seconds</b> for hourly capacity monitoring.
    * <b>7200 seconds</b> for long-term scaling trend review.

# Use Cases Example <a name="example"></a>
## Use Case 1: Validating Auto Scaling Policy Behavior <a name="example-1"></a>
Monitoring <b>GroupDesiredCapacity</b> helps ensure that scaling policies set the correct desired instance count based on load or scheduled configurations.


## Use Case 2: Detecting Unintended Configuration Changes <a name="example-2"></a>
Unexpected modifications to desired capacity may indicate misconfigurations or automation issues. This metric helps identify such changes quickly.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Auto Scaling Metrics Documentation
https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html