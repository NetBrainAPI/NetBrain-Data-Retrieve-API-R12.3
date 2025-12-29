# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Performance Degradation in Object Retrieval](#example-1) 
    - [Use Case 2 -- Monitoring Application User Experience](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>First Byte Latency</b> metric measures the time, in milliseconds, between when Amazon S3 receives a request and when it starts returning the first byte of the response. This delay can indicate performance issues related to object retrieval, bucket configuration, backend processing, or network latency. Monitoring this metric ensures optimal application performance and helps detect bottlenecks affecting user experience.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: FirstByteLatency
* <b>Namespace</b>: AWS/S3
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: BucketName
* <b>Display Name in NetBrain</b>: First Byte Latency

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing response latency from S3. Useful for identifying spikes in retrieval time, validating performance SLAs, or diagnosing issues with specific objects or access patterns.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean time (in milliseconds) taken by S3 to return the first byte of data after receiving a request.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for fine-grained latency troubleshooting.
    * <b>3600 seconds</b> for hourly monitoring of S3 performance.
    * <b>7200 seconds</b> for long-term latency and access pattern evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Performance Degradation in Object Retrieval <a name="example-1"></a>
Increased <b>FirstByteLatency</b> may indicate slow backend operations, increased load on S3, or inefficient object access patterns.


## Use Case 2: Monitoring Application User Experience <a name="example-2"></a>
Applications relying on timely object retrieval—such as media delivery or API responses—benefit from tracking this metric to identify and minimize latency impacts.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS S3 CloudWatch Metrics Documentation
https://docs.aws.amazon.com/AmazonS3/latest/userguide/CloudWatchMetrics.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html