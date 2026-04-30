# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Aggregation Function](#aggregation-function)
- [Supported Functions](#supported-functions)
- [Evaluation Logic](#evaluation-logic)
- [Interpretation](#interpretation)
- [Success Criteria](#success-criteria)
- [Alert Criteria](#alert-criteria)
- [Use Case Examples](#use-case-examples)
- [Reference](#reference)


# Overview <a name="overview"></a>
The <b>Container Last Terminated Reason</b> API identifies the most recent termination reason for a container within a Kubernetes pod.

This metric helps diagnose why a container stopped previously. Common termination reasons include:

* OOMKilled
* Error
* Completed
* ContainerCannotRun

Understanding termination reasons is critical for troubleshooting application failures and instability.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_status_last_terminated_reason
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Gauge (label-based state indicator)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: max_over_time
* <b>Display Name in NetBrain</b>: Container Last Terminated Reason

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Reason (Optional Filter)
Defines specific termination reasons to monitor.

Examples:

* OOMKilled
* Error
* Completed
* ContainerCannotRun


## Time Range
Defines how far back to evaluate the termination state.

* Example: 5m, 15m
* Default: 5m



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* max_over_time(v range-vector)

## Rationale
Ensures detection if the termination reason occurred at any point in the selected time window.


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* max(v)
* count(v)

## Over-Time Aggregations
* max_over_time(v range-vector) (Default)
* min_over_time(v range-vector)
* count_over_time(v range-vector)
* changes(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
max_over_time(
  kube_pod_container_status_last_terminated_reason{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }[<time_range>]
) == 1
```

## Filtered for Critical Reasons (Recommended)
```
max_over_time(
  kube_pod_container_status_last_terminated_reason{
    namespace="$NAME_SPACE",
    pod="$KUBNAME",
    reason=~"OOMKilled|Error|ContainerCannotRun"
  }[<time_range>]
) == 1
```


# Interpretation <a name="interpretation"></a>
* Value = 1 → Container was last terminated due to the specified reason
* Value = 0 → No such termination reason observed


# Success Criteria <a name="success-criteria"></a>
No containers have been recently terminated due to critical failure reasons.

# Alert Criteria <a name="alert-criteria"></a>
A container has been terminated due to critical reasons such as OOMKilled, Error, or ContainerCannotRun within the evaluated time range. This indicates application instability or resource issues.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: OOM Detection
Identify containers terminated due to memory exhaustion.


## Use Case 2: Crash Analysis
Detect application failures resulting in container termination.


## Use Case 3: Deployment Validation
Ensure newly deployed containers are not failing immediately.


## Use Case 4: Root Cause Analysis
Correlate termination reasons with resource metrics and logs.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
