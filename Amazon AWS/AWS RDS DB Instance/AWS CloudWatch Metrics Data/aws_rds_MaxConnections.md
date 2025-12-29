# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Capacity Planning for Connection-Heavy Applications](#example-1) 
    - [Use Case 2 -- Detecting the Need for Scaling](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>MaxConnections</b> metric represents the maximum number of concurrent database connections allowed for an Amazon RDS instance.
This value depends on the database engine type, version, and instance class, and it is critical for assessing connection capacity and ensuring your applications do not exceed RDS connection limits.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: MaxConnections
* <b>Namespace</b>: AWS/RDS
* <b>Unit / Stat</b>: Maximum
* <b>Dimension</b>: DBInstanceIdentifier
* <b>Display Name in NetBrain</b>: DB Instance Max Connections

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing maximum connection capacity over a given period. Useful for validating whether the instance size is sufficient to support application workloads.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Maximum.
  * <b>Maximum</b>: Shows the highest number of maximum connections recorded during the selected time period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for short-term capacity evaluation.
    * <b>3600 seconds</b> for standard monitoring intervals.
    * <b>7200 seconds</b> for long-term planning and scaling decisions.

# Use Cases Example <a name="example"></a>
## Use Case 1: Capacity Planning for Connection-Heavy Applications <a name="example-1"></a>
Monitoring <b>MaxConnections</b> helps ensure that the database instance can support peak traffic without rejecting new connections.

## Use Case 2: Detecting the Need for Scaling <a name="example-2"></a>
If your actual <b>DatabaseConnections</b> approaches <b>MaxConnections</b>, it may be necessary to scale up the RDS instance class or optimize connection pooling.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS RDS Metrics Documentation
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html