# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Detecting Workflow Execution Issues](#example-1) 
    - [Use Case 2 -- Monitoring Workflow Reliability](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>Work Flow Failures</b> metric measures the number of workflow executions in Amazon Simple Workflow Service (SWF) that have failed during a given time period. Monitoring this metric helps detect workflow disruptions, identify issues in task coordination, and ensure reliable orchestration of distributed processes.



# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: WorkflowsFailed
* <b>Namespace</b>: AWS/SWF
* <b>Unit / Stat</b>: Count
* <b>Dimension</b>: Domain
* <b>Display Name in NetBrain</b>: Work Flow Failures

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time range for analyzing failed workflow executions. Useful for identifying system issues, debugging workflow activities, or correlating failures with deployment or configuration changes.
* <b>Statistics</b>: Default value is Count.
  * <b>Count</b>: Represents the number of workflow failures during each evaluation interval.
  * <b>Recommended Values</b>:
    * <b>300 seconds</b> for detailed workflow failure investigation.
    * <b>3600 seconds</b> for standard hourly failure monitoring.
    * <b>7200 seconds</b> for long-term reliability analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Detecting Workflow Execution Issues <a name="example-1"></a>
Spikes in <b>WorkflowsFailed</b> may indicate application logic errors, task failures, misconfigurations, or infrastructure issues affecting workflow steps.


## Use Case 2: Monitoring Workflow Reliability <a name="example-2"></a>
This metric helps ensure workflows are running successfully and consistently, supporting proactive troubleshooting and maintaining system resilience.

# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS SWF Metrics Documentation
https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-monitoring-cloudwatch.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html