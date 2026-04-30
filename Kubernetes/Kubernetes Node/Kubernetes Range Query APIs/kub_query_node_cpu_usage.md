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
The <b>Node CPU Utilization (Range)</b> API monitors CPU usage across Kubernetes nodes over a defined time range.

This API evaluates CPU consumption as a percentage of total available cores and provides a time-aggregated view of node CPU utilization. It helps detect sustained CPU pressure and performance degradation.

High CPU utilization over time may indicate:

* Resource exhaustion
* Inefficient workloads
* Scheduling imbalance


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: node_cpu_seconds_total
* <b>Source</b>: Prometheus (node exporter)
* <b>Metric Type</b>: Counter (converted to percentage using rate)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Base Function</b>: rate()
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Node CPU Usage

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Time Range
Defines how far back to evaluate CPU utilization.

* Example: 5m, 15m, 1h
* Default: 5m


## Unit
Defines the output format.

* Percentage (%)


## Rate Interval
Defines the window used inside the rate() function.

* Example: 1m, 2m, 5m
* Default: 2m



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a stable view of CPU usage and avoids noise from short-lived spikes.

## Threshold
Defines CPU utilization above which the node is considered under high load.

* Example: 80%
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
## PromQL Conceptual Expression
```
avg_over_time(
  (
    sum(rate(node_cpu_seconds_total{mode!="idle", instance="$DEV_IP"}[<rate_interval>]))
    /
    count(node_cpu_seconds_total{mode="system", instance="$DEV_IP"})
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
The CPU utilization of the node has exceeded the defined threshold over the evaluated time range. This condition may lead to performance degradation, increased latency, and reduced workload stability.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Sustained CPU Pressure Detection
Identify nodes experiencing prolonged high CPU usage.


## Use Case 2: Performance Monitoring
Track CPU trends over time for workload analysis.


## Use Case 3: Capacity Planning
Use historical CPU usage to guide scaling decisions.


## Use Case 4: Workload Distribution Optimization
Detect uneven CPU utilization across nodes.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Prometheus Node Exporter Metrics: https://prometheus.io/docs/guides/node-exporter/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
