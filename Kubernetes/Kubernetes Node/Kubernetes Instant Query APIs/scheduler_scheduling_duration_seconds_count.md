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
The <b>Scheduling Latency</b> API measures the time taken by the Kubernetes scheduler to assign pods to nodes.

End-to-end scheduling latency represents the duration between when a pod is created and when it is successfully scheduled onto a node. High latency may indicate inefficiencies in scheduling caused by:

* Resource constraints
* Node availability issues
* Scheduler bottlenecks
* Complex scheduling rules or filters

This API calculates the average scheduling latency per request over a defined interval.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: scheduler_framework_extension_point_duration_seconds
* <b>Components Used</b>:
  * _sum → total scheduling latency
  * _count → number of scheduling attempts
* <b>Filter</b>: extension_point="Filter"
* <b>Source</b>: Kubernetes Scheduler metrics
* <b>Metric Type</b>: Histogram (converted to average latency)
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: rate()
* <b>Display Name in NetBrain</b>: Scheduling Latency

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Rate Interval
Defines the time window used in rate calculation.

* Example: 1m, 5m, 10m
* Default: 5m


## Unit
Defines the output unit.

* Seconds (default)



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the latency above which scheduling is considered delayed.

* Example: 10 seconds
* Note: Threshold values should be tuned based on workload requirements.


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

## Range Functions (Used Internally)
* rate(v range-vector) (Primary)
* increase(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
avg(
  rate(scheduler_framework_extension_point_duration_seconds_sum{extension_point="Filter"}[<rate_interval>])
)
/
avg(
  rate(scheduler_framework_extension_point_duration_seconds_count{extension_point="Filter"}[<rate_interval>])
)
> <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → Scheduling latency is within acceptable limits
* Value above threshold → Scheduler is experiencing delays


# Success Criteria <a name="success-criteria"></a>
The scheduling latency has remained within the defined threshold at the time of evaluation.

# Alert Criteria <a name="alert-criteria"></a>
The scheduling latency exceeds the defined threshold, indicating delays in pod placement. This condition may be caused by resource constraints, scheduling complexity, or control plane performance issues.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Detecting Scheduling Delays
Identify when pods are taking longer than expected to be scheduled.


## Use Case 2: Resource Constraint Analysis
Correlate scheduling latency with insufficient CPU, memory, or node capacity.


## Use Case 3: Scheduler Performance Monitoring
Track efficiency of the scheduler over time.


## Use Case 4: Deployment Impact Analysis
Identify delays affecting application rollout and scaling operations.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Scheduler Metrics: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
