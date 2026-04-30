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
The <b>Scheduling Duration</b> API measures the time taken by the Kubernetes scheduler to process scheduling decisions for pods.

The metric scheduler_scheduling_duration_seconds represents the total time spent in scheduling operations. By calculating the average duration per scheduling attempt, this API helps identify delays in pod placement.

High scheduling duration may indicate:

* Resource constraints
* Node selection delays
* Scheduler performance bottlenecks
* High cluster load


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: scheduler_scheduling_duration_seconds
* <b>Components Used</b>:
  * _sum → total scheduling duration
  * _count → number of scheduling attempts
* <b>Source</b>: Kubernetes Scheduler metrics
* <b>Metric Type</b>: Histogram (converted to average duration)
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: rate()
* <b>Display Name in NetBrain</b>: Server Scheduling Duration

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Rate Interval
Defines the time window used in rate calculation.

* Example: 1m, 5m, 10m
* Default: 5m


## Unit
Defines the output unit.

* Seconds



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the scheduling duration above which delays are considered significant.

* Example: environment-specific (e.g., seconds range)
* Note: Threshold values depend on workload characteristics.


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
sum(
  rate(scheduler_scheduling_duration_seconds_sum[<rate_interval>])
)
/
sum(
  rate(scheduler_scheduling_duration_seconds_count[<rate_interval>])
)
> <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → Scheduling duration is within acceptable limits
* Value above threshold → Scheduling delays detected


# Success Criteria <a name="success-criteria"></a>
The scheduling duration has remained within the defined threshold at the time of evaluation.

# Alert Criteria <a name="alert-criteria"></a>
The scheduling duration exceeds the defined threshold, indicating delays in pod scheduling. This condition may result from resource constraints, scheduling complexity, or control plane performance issues.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Scheduler Performance Monitoring
Track how efficiently the scheduler is processing scheduling decisions.


## Use Case 2: Detecting Scheduling Bottlenecks
Identify delays caused by insufficient resources or complex scheduling rules.


## Use Case 3: Workload Deployment Analysis
Monitor the impact of scheduling delays on application rollout.


## Use Case 4: Control Plane Health Monitoring
Correlate scheduling delays with other control plane metrics such as API latency or etcd performance.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
