# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Capacity Shortages](#example-1) 
    - [Use Case 2 -- Troubleshooting Application Performance Issues](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Read Throttling Events</b> metric measures the number of throttled read requests for a DynamoDB table. Throttling occurs when a table or index receives more read requests than its provisioned or auto-scaled read capacity can handle. Monitoring this metric is essential for maintaining application performance, ensuring availability, and identifying capacity bottlenecks.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: ReadThrottleEvents
* <b>Namespace</b>: AWS/DynamoDB
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: TableName
* <b>Display Name in NetBrain</b>: Read Throttling Events

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing read throttling occurrences. This helps identify peak traffic periods or inadequate read capacity settings.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Represents the total number of read operations that were throttled during the specified period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed monitoring or troubleshooting throttling spikes.
    * <b>3600 seconds</b> for standard hourly trend visibility.
    * <b>7200 seconds</b> for long-term capacity planning.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Capacity Shortages <a name="example-1"></a>
Monitoring <b>ReadThrottleEvents</b> helps identify when a DynamoDB table requires increased Read Capacity Units (RCUs) or auto-scaling adjustments to support demand.



## Use Case 2: Troubleshooting Application Performance Issues <a name="example-2"></a>
Read throttling may cause increased latency or failed reads in applications. This metric helps pinpoint when throttling impacts user experience.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS DynamoDB Throttling Metric Documentation
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html