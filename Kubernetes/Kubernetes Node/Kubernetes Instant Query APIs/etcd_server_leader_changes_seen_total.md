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
The <b>etcd Leader Changes</b> API monitors the frequency of leader transitions within the etcd cluster.

The metric etcd_server_leader_changes_seen_total is a cumulative counter that increases whenever a new leader is elected. Frequent leader changes may indicate instability caused by:

* Network disruptions
* Resource contention
* Slow disk I/O
* Loss of quorum

This API evaluates the increase in leader changes over time to detect abnormal cluster behavior.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: etcd_server_leader_changes_seen_total
* <b>Source</b>: etcd metrics (Prometheus integration)
* <b>Metric Type</b>: Counter
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: increase()
* <b>Display Name in NetBrain</b>: Server Leader Changes

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Rate Interval
Defines the time window used to evaluate leader changes.

* Example: 5m, 10m, 15m
* Default: 5m


## Unit
Defines how the result is interpreted.

* Count (number of leader changes in the interval)



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the number of leader changes within the interval that indicates instability.

* Example: `> 3` changes in 5 minutes
* Note: Threshold values should be tuned based on cluster size and expected behavior.


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
* increase(v range-vector) (Primary)
* rate(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
sum(
  increase(
    etcd_server_leader_changes_seen_total[<rate_interval>]
  )
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value within threshold → Leader changes are within normal limits
* Value above threshold → Frequent leader transitions detected


# Success Criteria <a name="success-criteria"></a>
The number of etcd leader changes has remained within the defined threshold over the evaluated interval.

# Alert Criteria <a name="alert-criteria"></a>
The number of etcd leader changes has exceeded the defined threshold within the evaluated interval. This condition may indicate cluster instability caused by network issues, resource constraints, or quorum disruptions.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Detecting Cluster Instability
Identify frequent leader elections that may indicate unstable etcd behavior.


## Use Case 2: Network Issue Correlation
Correlate leader changes with network latency or packet loss.


## Use Case 3: Resource Constraint Detection
Detect CPU, memory, or disk pressure affecting etcd performance.


## Use Case 4: Control Plane Reliability Monitoring
Ensure stable leadership in etcd for consistent cluster operation.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* etcd Documentation: https://etcd.io/docs/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
