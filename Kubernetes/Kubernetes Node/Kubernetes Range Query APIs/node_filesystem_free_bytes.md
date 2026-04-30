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
The <b>Node Disk Free Space</b> API monitors the available disk space on Kubernetes nodes over a defined time range.

Disk availability is critical for:

* Pod scheduling
* Container runtime operations
* Log storage and image management

Low disk space can lead to:

* Pod evictions
* Node DiskPressure condition
* Application instability

This API evaluates free disk space over time to ensure nodes maintain sufficient storage capacity.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_filesystem_free_bytes
* <b>Source</b>: Prometheus (node exporter)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Disk Space Free

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate disk space.

* Example: 5m, 15m, 1h
* Default: 1h


## Unit
Defines how the metric is interpreted.

* bytes, KB, MB, GB
* percentage (recommended when normalized)



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a stable view of available disk space and avoids reacting to short-term fluctuations.

## Threshold
Defines the minimum free disk space.

* Can be defined as:
  * Absolute value (bytes)
  * Percentage of total disk (recommended)


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
## PromQL Conceptual Expression (Absolute Free Space)
```
avg_over_time(node_filesystem_free_bytes[<time_range>]) < <threshold>
```

## PromQL Conceptual Expression (Percentage-Based - Recommended)
```
avg_over_time(
  (
    node_filesystem_free_bytes
    /
    node_filesystem_size_bytes
    * 100
  )[<time_range>:]
) < <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value above threshold → Disk space is within acceptable limits
* Value below threshold → Node is running low on disk space


# Success Criteria <a name="success-criteria"></a>
The available disk space on the node has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The available disk space on the node has fallen below the defined threshold over the evaluated time range. This condition may lead to pod evictions, disk pressure conditions, and degraded node performance.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Preventing Disk Exhaustion
Detect low disk space before it impacts workloads.


## Use Case 2: Node Health Monitoring
Ensure nodes maintain sufficient storage capacity.


## Use Case 3: Capacity Planning
Track disk usage trends over time.


## Use Case 4: Storage Optimization
Identify nodes with uneven disk utilization.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
