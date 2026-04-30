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
The <b>Controller Manager Queue Duration</b> API measures the time items spend waiting in the controller manager workqueue before being processed.

Kubernetes controllers rely on workqueues to process events such as:

* Pod creation and updates
* Node lifecycle changes
* ReplicaSet and Deployment reconciliation

An increase in queue duration indicates that items are waiting longer before being processed, which may signal controller bottlenecks or system pressure.

This API calculates the average queue wait time per item over a defined interval.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: workqueue_queue_duration_seconds
* <b>Components Used</b>:
  * _sum → total queue wait time
  * _count → number of processed items
* <b>Source</b>: Kubernetes Controller Manager metrics
* <b>Metric Type</b>: Histogram (converted to average duration)
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: rate()
* <b>Display Name in NetBrain</b>: Server Workqueue Queue Duration (Performance)

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
Defines the queue duration above which controller performance is considered degraded.

* Example: 5 seconds
* Note: Threshold values should be tuned based on controller workload and cluster size.


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
  rate(workqueue_queue_duration_seconds_sum[<rate_interval>])
)
/
sum(
  rate(workqueue_queue_duration_seconds_count[<rate_interval>])
)
> <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → Queue processing latency is within acceptable limits
* Value above threshold → Controller processing delays or backlog detected


# Success Criteria <a name="success-criteria"></a>
The controller manager queue duration has remained within the defined threshold at the time of evaluation.

# Alert Criteria <a name="alert-criteria"></a>
The controller manager queue duration exceeds the defined threshold, indicating delays in processing queued items. This condition may result in slower reconciliation loops, delayed state convergence, and degraded cluster responsiveness.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Controller Bottleneck Detection
Identify delays in controller processing pipelines.


## Use Case 2: Backlog Monitoring
Detect buildup of unprocessed items in workqueues.


## Use Case 3: Control Plane Performance Analysis
Correlate queue delays with API server latency or etcd performance.


## Use Case 4: Troubleshooting Reconciliation Delays
Investigate delayed updates in deployments, nodes, or other resources.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
