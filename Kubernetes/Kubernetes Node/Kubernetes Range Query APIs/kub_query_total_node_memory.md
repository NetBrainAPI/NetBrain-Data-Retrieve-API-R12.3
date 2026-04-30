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
The <b>Node Memory Total (Range)</b> API provides the total memory capacity available on a Kubernetes node over a defined time range.

This metric represents the total physical memory of the node and serves as a baseline for:

* Memory utilization calculations
* Capacity planning
* Resource allocation analysis

While this metric does not indicate pressure or usage on its own, it is required to compute memory usage percentages and evaluate node health.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_memory_MemTotal_bytes
* <b>Source</b>: Prometheus (node exporter)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Node Memory Total

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate total memory.

* Example: 5m, 15m, 1h
* Default: 1h


## Unit
Defines how the metric is displayed.

* bytes
* KB / MB / GB



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Total memory is typically constant, but aggregation ensures consistency in case of:

* Metric collection variations
* Node restarts or reporting inconsistencies


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
avg_over_time(node_memory_MemTotal_bytes[<time_range>])
```


# Interpretation <a name="interpretation"></a>
* Higher value → Larger total memory capacity
* Lower value → Smaller memory capacity

This metric is expected to remain stable under normal conditions.


# Success Criteria <a name="success-criteria"></a>
The total memory capacity of the node is successfully retrieved and remains consistent over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
Not typically applicable as a standalone alert. Unexpected changes in total memory may indicate node replacement, configuration changes, or underlying infrastructure issues.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Capacity Baseline
Establish total memory available per node.


## Use Case 2: Memory Utilization Calculation
Use in combination with:

* node_memory_MemAvailable_bytes

to compute memory usage percentage.


## Use Case 3: Infrastructure Validation
Verify expected memory configuration across nodes.


## Use Case 4: Trend Analysis
Track changes in node capacity due to scaling or infrastructure updates.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Prometheus Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
