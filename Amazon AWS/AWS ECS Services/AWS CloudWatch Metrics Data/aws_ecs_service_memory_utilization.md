# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Memory Pressure in ECS Services](#example-1) 
    - [Use Case 2 -- Detecting Memory Leaks or Inefficient Workloads](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>ECS Service Memory Utilization</b> metric measures the average percentage of memory consumed by tasks running within an ECS service. This metric helps assess service performance, identify memory constraints, and determine whether scaling or configuration adjustments are required to maintain stable and efficient operations.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: MemoryUtilization
* <b>Namespace</b>: AWS/ECS
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: ServiceName
* <b>Display Name in NetBrain</b>: Memory Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used to analyze memory usage trends for the service. This helps detect memory saturation, leaks, or configuration inefficiencies.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Indicates the mean memory utilization across all tasks in the service during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed memory monitoring during application load changes.
    * <b>3600 seconds</b> for hourly memory trend visibility.
    * <b>7200 seconds</b> for long-term service performance analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Memory Pressure in ECS Services <a name="example-1"></a>
Monitoring <b>MemoryUtilization</b> helps detect when services approach memory limits, which may require scaling, container reconfiguration, or workload optimization.


## Use Case 2: Detecting Memory Leaks or Inefficient Workloads <a name="example-2"></a>
A steady increase in memory usage may signal memory leaks or improperly configured containers. This metric helps pinpoint such issues early to avoid service disruption.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS ECS Service Memory Utilization Metric Documentation
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cloudwatch-metrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html