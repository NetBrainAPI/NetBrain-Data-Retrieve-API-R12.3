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
The <b>Pod Memory Usage (Range)</b> API monitors memory consumption of containers within a Kubernetes pod over a defined time range.

The metric container_memory_usage_bytes represents total memory usage, including cache. This provides visibility into overall memory consumption patterns of workloads.

High memory usage over time may indicate:

* Memory-intensive workloads
* Inefficient memory utilization
* Risk of memory pressure if limits are reached


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: container_memory_usage_bytes
* <b>Source</b>: cAdvisor (via kubelet / Prometheus)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Container Memory Usage

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Time Range
Defines how far back to evaluate memory usage.

* Example: 5m, 15m, 1h
* Default: 5m


## Unit
Defines how the metric is displayed.

* bytes
* MB / GB



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Rationale
Provides a stable view of memory usage and avoids reacting to short-lived fluctuations.

## Threshold
Defines memory usage above which the pod is considered under pressure.

Can be defined as:

* Absolute value (bytes)
* Percentage of memory limit (recommended)


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
  sum(
    container_memory_usage_bytes{
      namespace="$NAME_SPACE",
      pod="$KUBNAME",
      container!=""
    }
  )[<time_range>:]
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → Memory usage is within acceptable limits
* Value above threshold → Pod is consuming high memory


# Success Criteria <a name="success-criteria"></a>
The memory usage of the pod has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The memory usage of the pod has exceeded the defined threshold over the evaluated time range. This condition may lead to memory pressure, container restarts, or degraded application performance.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Memory Consumption Monitoring
Track total memory usage trends for workloads.


## Use Case 2: Detecting Memory Growth
Identify pods with steadily increasing memory usage.


## Use Case 3: Resource Optimization
Compare memory usage against requests and limits.


## Use Case 4: Capacity Planning
Understand workload memory requirements over time.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* cAdvisor Metrics: https://github.com/google/cadvisor
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
