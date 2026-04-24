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
The <b>Node Memory Availability (Instant Query)</b> API retrieves the current available memory for a Kubernetes node using a Prometheus instant query.

This API provides a point-in-time view of memory availability, which is useful for real-time monitoring and quick diagnostics. It can also be combined with derived calculations to evaluate memory usage as a percentage of total capacity.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_memory_MemAvailable_bytes
* <b>Related Metric</b>: node_memory_MemTotal_bytes
* <b>Source</b>: Prometheus (node exporter / kubelet metrics)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Node Memory Available Query

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Unit
Defines how the metric is interpreted or displayed.

* Supported: bytes, KB, MB, GB, percentage



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the minimum available memory threshold.

Can be defined as:

* Absolute value (bytes)
* Percentage of total memory (recommended)
* Note: Threshold values should be environment-specific.


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations (Applicable)
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
Not applicable at API level for instant queries.
If needed, these should be implemented using the range query API (QueryRangeMetrics).


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression (Absolute Memory)
```
node_memory_MemAvailable_bytes
```

## PromQL Conceptual Expression (Percentage-Based - Recommended)
```
(node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100
```


# Interpretation <a name="interpretation"></a>
* Value above threshold → Memory availability is within acceptable limits
* Value below threshold → Node may be under memory pressure


# Success Criteria <a name="success-criteria"></a>
The available memory of the node is within the defined threshold at the time of evaluation.

# Alert Criteria <a name="alert-criteria"></a>
The available memory of the node is below the defined threshold at the time of evaluation. This condition may indicate potential memory pressure and can lead to workload instability if sustained.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Real-Time Node Health Check
Quickly assess current memory availability on a node.


## Use Case 2: On-Demand Troubleshooting
Validate memory conditions during incidents or performance investigations.


## Use Case 3: Baseline Validation
Compare current memory state against expected thresholds.


## Use Case 4: Input for Composite APIs
Use this metric as a building block for higher-level health evaluations.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Querying Basics: https://prometheus.io/docs/prometheus/latest/querying/basics/
