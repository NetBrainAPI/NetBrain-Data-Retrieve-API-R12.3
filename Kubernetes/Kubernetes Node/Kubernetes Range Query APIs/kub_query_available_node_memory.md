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
The <b>Node Memory Availability (Range)</b> API monitors available memory on Kubernetes nodes over a defined time range.

Available memory represents the amount of memory that can be allocated to workloads without causing memory pressure. Monitoring this metric helps detect sustained low-memory conditions that may impact node stability.

Low memory availability can lead to:

* Pod evictions (OOMKill)
* Node MemoryPressure condition
* Application instability


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_memory_MemAvailable_bytes
* <b>Related Metric</b>: node_memory_MemTotal_bytes
* <b>Source</b>: Prometheus (node exporter)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Node Memory Available

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate available memory.

* Example: 5m, 15m, 1h
* Default: 5m


## Unit
Defines how the metric is interpreted.

* bytes, MB, GB
* percentage (recommended)



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a stable view of memory availability and avoids reacting to short-lived fluctuations.

## Threshold
Defines the minimum available memory.

* Can be defined as:
  * Absolute value (bytes)
  * Percentage of total memory (recommended)


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
## PromQL Conceptual Expression (Absolute Memory)
```
avg_over_time(node_memory_MemAvailable_bytes[<time_range>]) < <threshold>
```

## PromQL Conceptual Expression (Percentage-Based - Recommended)
```
avg_over_time(
  (
    node_memory_MemAvailable_bytes{instance="$DEV_IP"}
    /
    node_memory_MemTotal_bytes{instance="$DEV_IP"}
    * 100
  )[<time_range>:]
) < <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value above threshold → Memory availability is within acceptable limits
* Value below threshold → Node is under memory pressure


# Success Criteria <a name="success-criteria"></a>
The available memory of the node has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The available memory of the node has fallen below the defined threshold over the evaluated time range. This condition may lead to pod evictions, application instability, and reduced node reliability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Sustained Memory Pressure Detection
Identify nodes with consistently low available memory.


## Use Case 2: Node Stability Monitoring
Ensure nodes maintain sufficient memory capacity for workloads.


## Use Case 3: Capacity Planning
Analyze memory trends to plan scaling or optimization.


## Use Case 4: Workload Optimization
Detect memory-intensive workloads affecting node performance.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
