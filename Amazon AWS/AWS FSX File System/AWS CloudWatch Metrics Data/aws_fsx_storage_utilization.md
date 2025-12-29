# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Preventing File System Capacity Exhaustion](#example-1) 
    - [Use Case 2 -- Capacity Planning and Usage Optimization](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>FSx Storage Utilization</b> metric measures the amount of free storage capacity available on an AWS FSx file system. Monitoring this metric helps identify when the file system is approaching its storage limits, enabling proactive scaling, cleanup operations, and ensuring uninterrupted file system performance.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: FreeStorageCapacity
* <b>Namespace</b>: AWS/FSx
* <b>Unit / Stat</b>: Bytes
* <b>Dimension</b>: FileSystemId
* <b>Display Name in NetBrain</b>: Storage Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing available storage capacity. Useful for detecting growth trends and predicting when additional storage will be required.
* <b>Statistics</b>: Default value is Bytes.
  * <b>Bytes</b>: Represents the available free storage capacity measured at each data point.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed monitoring of rapidly changing storage usage.
    * <b>3600 seconds</b> for hourly capacity oversight.
    * <b>7200 seconds</b> for long-term storage planning.

# Use Cases Example <a name="example"></a>
## Use Case 1: Preventing File System Capacity Exhaustion <a name="example-1"></a>
Monitoring <b>FreeStorageCapacity</b> helps identify when available storage is running low, allowing administrators to expand storage or delete unnecessary data before performance issues occur.


## Use Case 2: Capacity Planning and Usage Optimization <a name="example-2"></a>
Tracking changes in free storage over time supports forecasting future storage requirements and optimizing data lifecycle management strategies.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS FSx Storage Capacity Metric Documentation
https://docs.aws.amazon.com/fsx/latest/WindowsGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html