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
The <b>Node CPU Utilization</b> API monitors CPU usage across Kubernetes nodes to detect sustained resource pressure and potential performance degradation.

High CPU utilization may lead to increased latency, workload throttling, and reduced scheduling efficiency. This API evaluates CPU consumption over time to ensure nodes operate within acceptable limits.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_cpu_seconds_total
* <b>Source</b>: Prometheus (node exporter / kubelet metrics)
* <b>Metric Type</b>: Counter (converted to percentage using rate)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Base Function</b>: rate()
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Node CPU Utilization

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate CPU utilization.

* Example: 5m, 15m, 1h
* Default: 5m


## Unit
Defines the granularity of evaluation.

* Supported: seconds, minutes, hours


## Rate Interval
Defines the range used inside the rate() calculation.

* Example: 1m, 2m, 5m
* Default: 2m



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a stable view of CPU usage and avoids alerting on short-lived spikes.

## Threshold
Defines the CPU utilization percentage above which the node is considered under high load.

* Example: 80%
* Note: Threshold values should be defined based on workload requirements.


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
avg_over_time(
  (
    sum(rate(node_cpu_seconds_total{mode!="idle"}[<rate_interval>])) by (instance)
    /
    count(node_cpu_seconds_total{mode="system"}) by (instance)
    * 100
  )[<time_range>:]
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → CPU utilization is within acceptable limits
* Value above threshold → Node is under sustained CPU pressure


# Success Criteria <a name="success-criteria"></a>
The CPU utilization of the node has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The CPU utilization of the node has exceeded the defined threshold over the evaluated time range. This condition may result in performance degradation, increased latency, and reduced workload stability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Sustained CPU Pressure Detection
Identify nodes experiencing prolonged high CPU usage.


## Use Case 2: Performance Degradation Analysis
Correlate CPU saturation with application latency or failures.


## Use Case 3: Capacity Planning
Track CPU trends to guide scaling decisions.


## Use Case 4: Workload Distribution Optimization
Detect imbalanced workloads across nodes.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
* Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
