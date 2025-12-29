# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Identifying Client-Side or Access Issues](#example-1) 
    - [Use Case 2 -- Validating Application or API Changes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>4xx Errors</b> metric tracks the number of HTTP 4xx client errors encountered when accessing objects stored in an Amazon S3 bucket. These errors typically result from invalid requests, missing objects, unauthorized access, or malformed request parameters. Monitoring this metric helps detect client-side issues, misconfigurations, and access-related failures.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: 4xxErrors
* <b>Namespace</b>: AWS/S3
* <b>Unit / Stat</b>: Sum
* <b>Dimension</b>: BucketName
* <b>Display Name in NetBrain</b>: 4xx Errors

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the timeframe for analyzing client error occurrences when interacting with the S3 bucket. Helpful for troubleshooting user access issues, broken links, or application misbehavior.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Sum.
  * <b>Sum</b>: Represents the total count of 4xx client-side errors during the selected period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for fine-grained error monitoring.
    * <b>3600 seconds</b> for hourly error rate tracking.
    * <b>7200 seconds</b> for long-term access pattern and error trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Identifying Client-Side or Access Issues <a name="example-1"></a>
A rise in <b>4xxErrors</b> may indicate unauthorized access attempts, missing objects (404), or incorrect request syntax.


## Use Case 2: Validating Application or API Changes <a name="example-2"></a>
An increase in client errors following a deployment may suggest incorrect object paths, permissions misconfigurations, or broken references in applications.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS S3 CloudWatch Metrics Documentation
https://docs.aws.amazon.com/AmazonS3/latest/userguide/CloudWatchMetrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html