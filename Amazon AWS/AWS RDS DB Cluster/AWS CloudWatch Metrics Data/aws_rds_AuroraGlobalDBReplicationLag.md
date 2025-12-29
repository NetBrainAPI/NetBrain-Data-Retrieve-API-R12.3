# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Ensuring Cross-Region Data Consistency](#example-1) 
    - [Use Case 2 -- Detecting Network or Workload Bottlenecks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Global DB Replication Lag</b> metric measures the average amount of replication delay, in milliseconds, between the primary cluster and replica DB clusters in an Amazon Aurora Global Database. Monitoring this metric is vital for ensuring cross-region data consistency, minimizing replication delays, and maintaining high-performance global read infrastructure.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: AuroraGlobalDBReplicationLag
* <b>Namespace</b>: AWS/RDS
* <b>Unit / Stat</b>: Average
* <b>Dimension</b>: DBClusterIdentifier
* <b>Display Name in NetBrain</b>: Global DB Replication Lag

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period used to analyze CPU usage. Useful for identifying load peaks, tuning performance, and diagnosing query or workload inefficiencies.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Average.
  * <b>Average</b>: Represents the mean replication lag in milliseconds during the selected time window.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for real-time replication lag analysis.
    * <b>3600 seconds</b> for hourly performance monitoring.
    * <b>7200 seconds</b> for long-term lag and network performance trend evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Ensuring Cross-Region Data Consistency <a name="example-1"></a>
Monitoring <b>AuroraGlobalDBReplicationLag</b> helps verify that replica clusters remain up-to-date, which is critical for global read scaling and disaster recovery readiness.


## Use Case 2: Detecting Network or Workload Bottlenecks <a name="example-2"></a>
Increases in lag may indicate heavy write workloads, cross-region network latency, throttling, or replication bottlenecks. This metric helps pinpoint and troubleshoot such issues.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS RDS and Aurora Metrics Documentation
https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html