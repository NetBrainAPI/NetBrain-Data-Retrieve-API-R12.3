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
The <b>Node Memory Availability</b> API monitors the available memory on Kubernetes nodes to detect memory pressure conditions that may impact workload performance and stability.

Low available memory can lead to:

* Pod evictions (OOMKill)
* Application instability
* Node pressure conditions (MemoryPressure)
* Scheduling constraints

This API evaluates available memory over time to ensure nodes maintain sufficient capacity for workloads.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_memory_MemAvailable_bytes
* <b>Source</b>: Prometheus (node exporter / kubelet metrics)
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
Defines the granularity of evaluation.

* Supported: seconds, minutes, hours



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a stable view of memory availability and avoids reacting to short-lived fluctuations.

## Threshold
Defines the minimum available memory threshold.

Can be defined as:

* Absolute value (bytes)
* Percentage of total memory (recommended for normalization)
* Note: Threshold values should be environment-specific.


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
    node_memory_MemAvailable_bytes
    /
    node_memory_MemTotal_bytes
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
## Use Case 1: Preventing OOM Events
Detect low memory conditions before workloads are terminated due to insufficient memory.


## Use Case 2: Node Health Monitoring
Track memory availability to ensure nodes are operating within safe limits.


## Use Case 3: Capacity Planning
Analyze memory consumption trends to plan scaling strategies.


## Use Case 4: Workload Optimization
Identify memory-intensive workloads affecting node stability.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
