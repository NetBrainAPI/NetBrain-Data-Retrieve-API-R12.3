# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Service Performance Health](#example-1) 
    - [Use Case 2 -- Identifying Overloaded or Inefficient Tasks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>ECS Service CPU Utilization</b> metric measures the average Averageage of CPU consumed by tasks running under a specific ECS service. Monitoring this metric is essential for ensuring service performance, balancing workloads across tasks, and determining when scaling actions are required to maintain responsiveness.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CPUUtilization
* <b>Namespace</b>: AWS/ECS
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: ServiceName
* <b>Display Name in NetBrain</b>: CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Specifies the time range for analyzing service-level CPU usage patterns. Useful for detecting service performance issues or validating scaling behaviors.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean CPU usage across all tasks in the service for the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for granular CPU monitoring during scaling events.
    * <b>3600 seconds</b> for hourly tracking of service performance.
    * <b>7200 seconds</b> for long-term CPU utilization analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Service Performance Health <a name="example-1"></a>
Tracking <b>CPUUtilization</b> helps identify when a service is under heavy load, supporting better decisions around task count scaling or resource allocation.


## Use Case 2: Identifying Overloaded or Inefficient Tasks <a name="example-2"></a>
High CPU usage may indicate poorly optimized workloads, unexpected traffic spikes, or inefficient container configurations. This metric helps diagnose task-level performance issues.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS ECS Service CPU Utilization Metric Documentation
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cloudwatch-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html