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
The <b>Node Status Check</b> API monitors the readiness state of Kubernetes nodes to detect nodes that are unavailable or not functioning correctly.

A node is considered healthy when its Ready condition is true. If a node transitions to a NotReady state, it may indicate:

* Node failure or shutdown
* Network or connectivity issues
* Kubelet malfunction
* Resource exhaustion

This API evaluates node readiness over time to ensure consistent cluster availability.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_node_status_condition
* <b>Filter</b>: {condition="Ready", status="true"}
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Binary (1 = Ready, 0 = Not Ready)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: min_over_time
* <b>Display Name in NetBrain</b>: Node Status Check

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate node readiness.

* Example: 5m, 15m, 1h
* Default: 5m


## Unit
Defines the granularity of evaluation.

* Supported: seconds, minutes, hours



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* min_over_time(v range-vector)

## Rationale
Ensures strict validation of node availability. If a node was in a NotReady state at any point during the time range, the result reflects the failure condition.


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
min_over_time(
  kube_node_status_condition{condition="Ready", status="true"}[<time_range>]
)
```


# Interpretation <a name="interpretation"></a>
* Value = 1 → Node has remained in Ready state throughout the time range
* Value = 0 → Node was NotReady at some point during the time range


# Success Criteria <a name="success-criteria"></a>
The node has remained in a Ready state within the defined time range.

# Alert Criteria <a name="alert-criteria"></a>
The node has entered a NotReady state within the defined time range. This condition may indicate node failure, connectivity issues, or resource constraints, and can impact workload availability and cluster stability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Node Availability Monitoring
Ensure all nodes remain consistently available in the cluster.


## Use Case 2: Detecting Intermittent Node Failures
Identify nodes that temporarily drop out of the Ready state.


## Use Case 3: Cluster Stability Assurance
Validate node health as part of overall cluster reliability monitoring.


## Use Case 4: Incident Correlation
Correlate node readiness issues with application disruptions or scheduling failures.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
