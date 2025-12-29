# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Backend or Service Failures](#example-1) 
    - [Use Case 2 -- Validating Deployment or Configuration Changes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>HTTP 500 Response Count</b> metric measures the number of HTTP 5XX responses returned by an AWS VPC Lattice service. HTTP 5XX errors indicate server-side issues, such as backend failures, misconfigurations, or performance bottlenecks. Monitoring this metric helps ensure service reliability and supports diagnosing internal service failures.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: HTTPCode_5XX_Count
* <b>Namespace</b>: AWS/VpcLattice
* <b>Unit / Stat</b>: Count
* <b>Dimension</b>: Service
* <b>Display Name in NetBrain</b>: HTTP 500 Response Count

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for analyzing server-side failure responses. Useful for identifying system instability, backend failures, or deployment-related issues.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Count.
  * <b>Count</b>: Represents the total number of HTTP 5XX responses returned by the service during each interval
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed real-time error analysis.
    * <b>3600 seconds</b> for hourly service health tracking.
    * <b>7200 seconds</b> for long-term reliability evaluation.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Backend or Service Failures <a name="example-1"></a>
A rise in <b>HTTPCode_5XX_Count</b> may indicate server-side issues such as overloaded resources, failing dependencies, or misconfigurations within the VPC Lattice service.


## Use Case 2: Validating Deployment or Configuration Changes <a name="example-2"></a>
Spikes in 5XX errors immediately after deployments can signal misconfigurations, code defects, or integration issues. This metric helps identify such problems quickly.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS VPC Lattice Metrics Documentation
https://docs.aws.amazon.com/vpc-lattice/latest/ug/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html

