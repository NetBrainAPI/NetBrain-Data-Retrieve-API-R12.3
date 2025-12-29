# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring Database Load](#example-1) 
    - [Use Case 2 -- Identifying Application Connection Leaks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>DatabaseConnections</b> metric tracks the number of active database connections currently being used by an Amazon RDS instance.
Monitoring this metric helps evaluate application load, connection pooling efficiency, and potential bottlenecks related to database performance or resource limits.
# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: DatabaseConnections
* <b>Namespace</b>: AWS/RDS
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DBInstanceIdentifier
* <b>Display Name in NetBrain</b>: DB Instance Database Connections

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period over which database connection activity is analyzed. Useful for performance tuning, detecting spikes, or reviewing load patterns.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Shows the mean number of active connections during the monitoring period.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time troubleshooting of connection saturation.
    * <b>3600 seconds</b> to observe general usage trends.
    * <b>7200 seconds</b> for hourly usage patterns and long-term analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring Database Load <a name="example-1"></a>
Tracking connection counts helps ensure that your RDS instance is sized correctly and prevents throttling due to exceeding max_connections limits.

## Use Case 2: Identifying Application Connection Leaks <a name="example-2"></a>
An unexpected gradual increase in connections may indicate improper connection closing or issues with connection pooling libraries.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS RDS Metrics Documentation
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html