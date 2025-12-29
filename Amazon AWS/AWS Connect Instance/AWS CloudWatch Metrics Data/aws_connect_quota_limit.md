# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Capacity Overload](#example-1) 
    - [Use Case 2 -- Protecting Customer Experience](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>AWS Connect Concurrency Quota Limit</b> metric measures the number of voice calls that exceeded the concurrent call limit configured for an Amazon Connect instance. When the instance has reached its maximum allowed number of simultaneous calls, any additional incoming or outgoing calls are blocked. Monitoring this metric helps identify when capacity is insufficient and ensures a smooth customer experience.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CallsBreachingConcurrencyQuota
* <b>Namespace</b>: AWS/Connect
* <b>Unit / Stat</b>: Count
* <b>Dimension</b>: InstanceId
* <b>Display Name in NetBrain</b>: Connect Concurrency Quota Limit

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the window for analyzing quota breach events. Useful for identifying peak periods where call capacity is insufficient.
* <b>Statistics</b>: Default value is Count.
  * <b>Count</b>: Shows the number of calls that exceeded the concurrency limit during the selected period.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for short-interval monitoring.
    * <b>3600 seconds</b> for standard hourly visibility.
    * <b>7200 seconds</b> for long-duration trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Capacity Overload <a name="example-1"></a>
Track <b>CallsBreachingConcurrencyQuota</b> to determine when your Amazon Connect instance reaches or exceeds its concurrency limit. Frequent events may indicate the need for a quota increase or traffic redirection.


## Use Case 2: Protecting Customer Experience <a name="example-2"></a>
Monitoring this metric helps ensure customers are not being rejected due to concurrency limits. Spikes may highlight unexpected call surges or inefficient routing strategies.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Connect Quota Limit Metric Documentation
https://docs.aws.amazon.com/connect/latest/adminguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html