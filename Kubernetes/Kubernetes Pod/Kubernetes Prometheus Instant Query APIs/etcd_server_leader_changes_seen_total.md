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
The <b>etcd Pod Leader Changes</b> API monitors the number of leader transitions observed by a specific etcd pod over time.

The metric etcd_server_leader_changes_seen_total is a cumulative counter that increases whenever a new leader is elected in the etcd cluster. Frequent leader changes may indicate instability caused by:

* Network connectivity issues
* Resource contention (CPU, memory, disk I/O)
* Loss of quorum
* Control plane disruptions

This API evaluates the rate of leader changes for a specific etcd pod to detect abnormal behavior.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: etcd_server_leader_changes_seen_total
* <b>Source</b>: etcd metrics (Prometheus)
* <b>Metric Type</b>: Counter
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: increase()
* <b>Display Name in NetBrain</b>: Server Leader Changes

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the namespace where etcd pod is running (typically kube-system).


## Pod Name
Defines the specific etcd pod.


## Rate Interval
Defines the time window to evaluate leader changes.

* Example: 5m, 10m, 15m
* Default: 5m


## Unit
Defines the output.

* Count (number of leader changes in interval)



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the number of leader changes indicating instability.

* Example: `> 3` changes in 5 minutes
* Note: Should be tuned based on cluster behavior


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
increase(
  etcd_server_leader_changes_seen_total{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }[<rate_interval>]
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value within threshold → Leader changes are within normal limits
* Value above threshold → Frequent leader transitions detected


# Success Criteria <a name="success-criteria"></a>
The number of leader changes observed by the etcd pod remains within the defined threshold over the evaluated interval.

# Alert Criteria <a name="alert-criteria"></a>
The number of leader changes observed by the etcd pod exceeds the defined threshold within the evaluated interval. This condition may indicate instability in the etcd cluster due to network issues, resource constraints, or quorum disruptions.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: etcd Stability Monitoring
Detect instability in etcd leadership behavior.


## Use Case 2: Network Issue Correlation
Identify leader changes caused by network latency or partitioning.


## Use Case 3: Control Plane Health Analysis
Correlate leader changes with API server or scheduler issues.


## Use Case 4: Pod-Level Diagnostics
Analyze which etcd member is frequently involved in leader transitions.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* etcd Documentation: https://etcd.io/docs/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
