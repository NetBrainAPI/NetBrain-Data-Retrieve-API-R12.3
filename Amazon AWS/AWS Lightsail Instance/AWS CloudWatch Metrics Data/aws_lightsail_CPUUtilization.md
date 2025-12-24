# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Ensuring Instance Performance and Stability](#example-1) 
    - [Use Case 2 -- Troubleshooting Workload Spikes](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>CPU Utilization</b> metric measures the percentage of allocated compute units currently being used by an Amazon Lightsail instance. Monitoring CPU utilization helps ensure that the instance has sufficient compute resources to handle its workload, detect overutilization or performance bottlenecks, and determine whether scaling or instance size adjustments may be necessary.

# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: CPUUtilization
* <b>Namespace</b>: AWS/Lightsail
* <b>Unit / Stat</b>: Maximum
* <b>Dimension</b>: InstanceName
* <b>Display Name in NetBrain</b>: CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time period for analyzing CPU usage behavior. Useful for detecting high-load bursts, workload inefficiencies, or performance degradation.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Maximum.
  * <b>Maximum</b>: Indicates the peak CPU utilization percentage recorded during the selected time interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for fine-grained detection of CPU spikes.
    * <b>3600 seconds</b> for standard hourly monitoring.
    * <b>7200 seconds</b> for long-term capacity trending.

# Use Cases Example <a name="example"></a>
## Use Case 1: Ensuring Instance Performance and Stability <a name="example-1"></a>
Monitoring <b>CPUUtilization</b> helps identify when the Lightsail instance is nearing CPU saturation, potentially requiring workload optimization or instance resizing.

## Use Case 2: Troubleshooting Workload Spikes <a name="example-2"></a>
High CPU peaks may indicate inefficient code execution, unexpected traffic surges, or background processes causing load. This metric assists in isolating such issues.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS Lightsail Metrics Documentation
https://docs.aws.amazon.com/lightsail/latest/userguide/monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html