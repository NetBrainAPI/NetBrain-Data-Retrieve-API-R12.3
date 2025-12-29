# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Write Capacity Bottlenecks](#example-1) 
    - [Use Case 2 -- Troubleshooting Write Latency or Failures](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Write Throttling Events</b> metric measures the number of throttled write requests for a DynamoDB table. Throttling occurs when the write request rate exceeds the table’s provisioned or auto-scaled write capacity. Tracking this metric is essential for maintaining consistent application performance and preventing failed or delayed write operations.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: WriteThrottleEvents
* <b>Namespace</b>: AWS/DynamoDB
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: TableName
* <b>Display Name in NetBrain</b>: Write Throttling Events

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing throttled write events. Useful for identifying capacity constraints during high write-load periods.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total number of throttled write operations during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed throttling investigation.
    * <b>3600 seconds</b> for typical hourly monitoring.
    * <b>7200 seconds</b> for long-term write performance trends.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Write Capacity Bottlenecks <a name="example-1"></a>
Monitoring <b>WriteThrottleEvents</b> helps identify when your DynamoDB table requires increased Write Capacity Units (WCUs) or auto-scaling adjustments to meet demand.


## Use Case 2: Troubleshooting Write Latency or Failures <a name="example-2"></a>
Write throttling may cause delays or failed write operations in applications. This metric helps pinpoint the cause of write-related performance degradation.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS DynamoDB Throttling Metric Documentation
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html