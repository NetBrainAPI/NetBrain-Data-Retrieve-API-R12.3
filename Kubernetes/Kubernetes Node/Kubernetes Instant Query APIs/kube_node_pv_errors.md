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
The <b>Persistent Volume (PV) Errors</b> API monitors Kubernetes events related to persistent volume failures that may impact application data availability.

Common error conditions include:

* FailedAttachVolume
* FailedMount
* VolumeResizeFailed

These errors indicate issues with storage provisioning, attachment, mounting, or resizing, which can prevent workloads from accessing required storage.

This API evaluates the frequency of such events over time to detect persistent storage issues.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_event_reason
* <b>Filter</b>: reason=~"FailedAttachVolume|FailedMount|VolumeResizeFailed"
* <b>Source</b>: kube-state-metrics / event exporter
* <b>Metric Type</b>: Counter (event occurrences)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Base Function</b>: increase()
* <b>Display Name in NetBrain</b>: Persistent Volume Errors

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines the window over which events are counted.

* Example: 5m, 10m, 1h
* Default: 5m


## Unit
Defines the evaluation granularity.

* Supported: seconds, minutes, hours



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the number of error events above which the condition is considered critical.

* Example: 3 events
* Note: Threshold values should be tuned based on workload sensitivity.


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* avg(v)
* min(v)
* max(v)
* count(v)
* stddev(v)
* stdvar(v)
* topk(k, v)
* bottomk(k, v)
* quantile(q, v)

## Over-Time / Range Functions
* increase(v range-vector) (Primary)
* rate(v range-vector)
* sum_over_time(v range-vector)
* count_over_time(v range-vector)
* changes(v range-vector)
* absent_over_time(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
sum(
  increase(
    kube_event_reason{reason=~"FailedAttachVolume|FailedMount|VolumeResizeFailed"}[<time_range>]
  )
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → PV-related errors are within acceptable limits
* Value above threshold → Frequent storage-related failures detected


# Success Criteria <a name="success-criteria"></a>
The number of persistent volume-related error events has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The number of persistent volume-related error events has exceeded the defined threshold over the evaluated time range. This condition may indicate storage system issues affecting volume attachment, mounting, or resizing, which can impact application availability and data access.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Storage Failure Detection
Identify recurring volume attachment or mount failures impacting workloads.


## Use Case 2: Incident Troubleshooting
Correlate application failures with underlying persistent volume errors.


## Use Case 3: Storage System Health Monitoring
Track error patterns to detect issues in underlying storage infrastructure.


## Use Case 4: Proactive Alerting
Detect repeated storage failures before they impact multiple workloads.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Events API: https://kubernetes.io/docs/reference/generated/kubernetes-api/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
