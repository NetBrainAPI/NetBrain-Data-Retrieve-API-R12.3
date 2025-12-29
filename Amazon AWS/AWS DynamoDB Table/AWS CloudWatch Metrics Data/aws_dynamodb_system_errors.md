# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying AWS-Side Service Issues](#example-1) 
    - [Use Case 2 -- Validating Request Integrity and Application Behavior](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>System Errors</b> metric tracks the number of requests to a DynamoDB table that resulted in AWS-side system errors. These errors may occur due to internal service issues, validation failures, or temporary system unavailability. Monitoring this metric is essential for identifying backend issues within DynamoDB that can impact application reliability and performance.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: SystemErrors
* <b>Namespace</b>: AWS/DynamoDB
* <b>Unit / Stat</b>: SampleCount
* <b>Dimension</b>: TableName
* <b>Display Name in NetBrain</b>: System Errors

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the analysis window for detecting DynamoDB system-level errors. Helps correlate error spikes with application activity or AWS events.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is SampleCount.
  * <b>SampleCount</b>: Shows the total number of system-level errors that occurred during the selected time frame.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for granular debugging of system issues.
    * <b>3600 seconds</b> for hourly system stability tracking.
    * <b>7200 seconds</b> for long-term error trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying AWS-Side Service Issues <a name="example-1"></a>
Monitoring <b>SystemErrors</b> helps detect when DynamoDB is experiencing internal faults, which may impact application operations. Elevated counts may require contacting AWS Support or checking service health dashboards.


## Use Case 2: Validating Request Integrity and Application Behavior <a name="example-2"></a>
Some system errors can be triggered by invalid request structures or schema mismatches. This metric assists in pinpointing malformed requests that result in backend validation failures.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS DynamoDB System Errors Metric Documentation
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html