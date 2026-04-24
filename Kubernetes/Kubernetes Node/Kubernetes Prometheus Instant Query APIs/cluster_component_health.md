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
The <b>Cluster Component Health (etcd)</b> API monitors the availability and health of etcd endpoints over a defined time range.

etcd is the primary datastore for Kubernetes cluster state. If etcd becomes unavailable or unhealthy, the control plane may fail to read or persist cluster data, which can result in API failures, scheduling issues, and overall cluster instability.

This API evaluates etcd endpoint health over time to ensure continuous availability of the control plane datastore.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: etcd_endpoint_health
* <b>Source</b>: etcd metrics (exporter or integration)
* <b>Metric Type</b>: Binary (1 = up, 0 = down)
* <b>Default Aggregation</b>: min_over_time
* <b>Display Name in NetBrain</b>: Cluster Component Health

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate etcd endpoint health.

* Example: 5m, 1h, 24h
* Default: 24h


## Unit
Defines the granularity of evaluation.

* Supported: seconds, minutes, hours



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* min_over_time(v range-vector)

## Rationale
Ensures strict validation of availability. If any etcd endpoint reports a down state during the selected time range, the result reflects the failure condition. This is appropriate for critical control plane components.


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

## Over-Time Aggregations
* min_over_time(v range-vector) (Default)
* avg_over_time(v range-vector)
* max_over_time(v range-vector)
* sum_over_time(v range-vector)
* count_over_time(v range-vector)
* quantile_over_time(q, v)
* stddev_over_time(v)
* stdvar_over_time(v)
* changes(v range-vector)
* absent_over_time(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
min_over_time(etcd_endpoint_health[<time_range>])
```


# Interpretation <a name="interpretation"></a>
* Value = 1 → etcd endpoints were continuously available during the time range
* Value = 0 → At least one etcd endpoint was unavailable during the time range


# Success Criteria <a name="success-criteria"></a>
The etcd endpoints have remained available within the defined time range for the cluster.

# Alert Criteria <a name="alert-criteria"></a>
The etcd endpoints have experienced unavailability within the defined time range. This condition may lead to partial or complete loss of cluster state access and can impact API operations, controller behavior, and control plane stability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Control Plane Availability Monitoring
Validate that etcd has remained continuously available over a defined operational window.


## Use Case 2: Detecting Intermittent Failures
Identify transient etcd outages that may not be visible through point-in-time checks.


## Use Case 3: Cluster Stability Assurance
Ensure that the datastore supporting Kubernetes state remains consistently accessible.


## Use Case 4: Root Cause Analysis
Correlate etcd availability issues with control plane symptoms such as API failures or delayed reconciliation.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* etcd Documentation: https://etcd.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
