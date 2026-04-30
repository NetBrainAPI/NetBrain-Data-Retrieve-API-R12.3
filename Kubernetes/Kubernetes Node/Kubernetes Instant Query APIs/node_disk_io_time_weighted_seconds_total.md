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
The <b>Persistent Volume Disk Pressure</b> API monitors disk utilization on Kubernetes nodes to detect disk pressure conditions that may impact workload stability.

Disk pressure occurs when a node is low on available disk space or inodes. When this happens:

* Kubernetes may evict lower-priority pods
* The node is marked with a DiskPressure condition
* New pods may not be scheduled onto the node
* Kubelet may perform garbage collection to reclaim space

This API evaluates disk usage over time and determines whether it exceeds a defined threshold.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_filesystem_usage
* <b>Source</b>: Node metrics (Prometheus / kubelet / node exporter)
* <b>Metric Type</b>: Percentage (0–100%)
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Disk Pressure

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate disk usage.

* Example: 5m, 1h, 24h
* Default: 1h


## Unit
Defines the granularity of evaluation.

* Supported: seconds, minutes, hours



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a balanced view of sustained disk usage and avoids noise from short-lived spikes.

## Threshold
Defines the disk usage percentage above which the node is considered under disk pressure.

* Example: 85%
* Note: Threshold values should be defined based on operational requirements and may vary by environment.


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
* avg_over_time(v range-vector) (Default)
* min_over_time(v range-vector)
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
avg_over_time(node_filesystem_usage[<time_range>]) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → Node disk usage is within acceptable limits
* Value above threshold → Node is experiencing disk pressure


# Success Criteria <a name="success-criteria"></a>
The node disk utilization has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The node disk utilization has exceeded the defined threshold over the evaluated time range. This condition may lead to pod evictions, scheduling constraints, and overall degradation of cluster stability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Preventing Pod Evictions
Detect sustained high disk usage before Kubernetes starts evicting pods.


## Use Case 2: Capacity Planning
Monitor long-term disk utilization trends to plan storage scaling.


## Use Case 3: Node Health Monitoring
Identify nodes under resource pressure that may affect workload scheduling.


## Use Case 4: Early Warning for Disk Exhaustion
Detect gradual disk consumption before it reaches critical levels.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Node Exporter: https://prometheus.io/docs/guides/node-exporter/
