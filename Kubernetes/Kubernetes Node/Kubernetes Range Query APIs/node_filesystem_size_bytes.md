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
The <b>Node Disk Space Total</b> API provides the total disk capacity available on a Kubernetes node.

This metric represents the full size of the filesystem and serves as a baseline for calculating:

* Disk utilization
* Available capacity
* Storage trends over time

While this metric alone does not indicate pressure or usage, it is essential for deriving percentage-based storage metrics and understanding node storage capacity.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_filesystem_size_bytes
* <b>Source</b>: Prometheus (node exporter)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Disk Space Total

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate total disk capacity.

* Example: 5m, 15m, 1h
* Default: 1h


## Unit
Defines how the metric is displayed.

* bytes
* KB / MB / GB
* Note: Conversion may be applied at visualization layer



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Disk size is generally static, but aggregation ensures consistency in cases where:

* Multiple filesystems are reported
* Transient reporting variations occur


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
avg_over_time(node_filesystem_size_bytes[<time_range>])
```


# Interpretation <a name="interpretation"></a>
* Higher value → Larger total disk capacity
* Lower value → Smaller disk capacity

This metric is typically stable and used as a reference baseline.


# Success Criteria <a name="success-criteria"></a>
The total disk capacity metric is successfully retrieved and remains consistent over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
Not typically applicable as a standalone alert. Sudden changes in total disk capacity may indicate configuration changes, node replacement, or underlying infrastructure issues.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Capacity Baseline
Establish total storage capacity for each node.


## Use Case 2: Disk Utilization Calculation
Use in combination with:

* node_filesystem_free_bytes
* node_filesystem_avail_bytes

to compute usage percentage.


## Use Case 3: Infrastructure Validation
Verify expected disk configuration across nodes.


## Use Case 4: Trend Analysis
Track changes in disk capacity due to scaling or infrastructure updates.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Prometheus Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
