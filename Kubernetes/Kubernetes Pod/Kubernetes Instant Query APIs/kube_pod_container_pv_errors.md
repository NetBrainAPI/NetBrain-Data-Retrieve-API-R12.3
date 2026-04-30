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
The <b>Persistent Volume (PV) Errors</b> API detects storage-related issues affecting Kubernetes pods by analyzing event metrics.

These errors typically occur when Kubernetes fails to:

* Attach volumes to nodes
* Mount volumes into containers
* Resize volumes

Common error reasons include:

* FailedAttachVolume
* FailedMount
* VolumeResizeFailed

Frequent occurrences of these events may lead to:

* Pod startup failures
* Application downtime
* Data access issues


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_event_reason
* <b>Source</b>: kube-state-metrics (events)
* <b>Metric Type</b>: Counter
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: increase()
* <b>Display Name in NetBrain</b>: Container Status PV Errors

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Error Reasons
Defines the storage-related failure reasons.

* FailedAttachVolume
* FailedMount
* VolumeResizeFailed


## Rate Interval
Defines the time window for event evaluation.

* Example: 5m, 10m
* Default: 5m



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the number of error events indicating an issue.

* Example: `> 3` events in 5 minutes


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* count(v)
* max(v)
* topk(k, v)

## Range Functions (Used Internally)
* increase(v range-vector) (Primary)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
sum(
  increase(
    kube_event_reason{
      namespace="$NAME_SPACE",
      pod="$KUBNAME",
      reason=~"FailedAttachVolume|FailedMount|VolumeResizeFailed"
    }[<rate_interval>]
  )
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Low or zero events → Storage operations are functioning normally
* Increasing events → Persistent volume issues detected


# Success Criteria <a name="success-criteria"></a>
No significant volume-related errors are observed for the pod within the evaluated interval.

# Alert Criteria <a name="alert-criteria"></a>
The number of persistent volume-related error events exceeds the defined threshold within the evaluated interval. This condition may indicate issues with volume attachment, mounting, or resizing, potentially leading to application disruption.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Pod Startup Failure Analysis
Detect pods failing to start due to volume issues.


## Use Case 2: Storage Reliability Monitoring
Track stability of persistent volume operations.


## Use Case 3: Troubleshooting Mount Issues
Identify failures in volume attachment or mounting.


## Use Case 4: Data Availability Assurance
Ensure applications have consistent access to storage.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Events: https://kubernetes.io/docs/reference/generated/kubernetes-api/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
