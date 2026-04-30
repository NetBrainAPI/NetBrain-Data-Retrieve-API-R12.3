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
The <b>etcd Leader Status</b> API monitors whether etcd cluster members recognize a leader.

The metric etcd_server_has_leader indicates leadership presence:

* 1 → the member recognizes a leader
* 0 → no leader is detected

etcd requires a leader to maintain cluster operations. If no leader is present, the cluster cannot process reads or writes, resulting in control plane failure.

This API evaluates the current leader status across etcd members to detect leadership loss conditions.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: etcd_server_has_leader
* <b>Source</b>: etcd metrics (Prometheus integration)
* <b>Metric Type</b>: Binary (1 = leader present, 0 = no leader)
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Server has Leader

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Unit
Defines how the metric is interpreted.

* Supported: binary (0 or 1)



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the expected value for healthy operation.

* Expected: 1
* Any value of 0 indicates a failure condition


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
If required, use a range query API for time-based validation.


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression (Per Node)
```
etcd_server_has_leader
```

## Cluster-Level Evaluation (Recommended)
```
min(etcd_server_has_leader)
```


# Interpretation <a name="interpretation"></a>
* Value = 1 → Leader is present and recognized
* Value = 0 → No leader detected

## Cluster-Level Interpretation
* At least one node reporting 1 → leader exists
* All nodes reporting 0 → no leader in cluster (critical condition)


# Success Criteria <a name="success-criteria"></a>
The etcd cluster has an active leader and members are able to recognize it.

# Alert Criteria <a name="alert-criteria"></a>
No etcd leader is detected across the cluster. This condition indicates loss of quorum or leadership failure and may result in inability to read or write cluster state, causing control plane disruption.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Control Plane Health Monitoring
Ensure that etcd leadership is maintained for normal cluster operations.


## Use Case 2: Detecting Quorum Loss
Identify situations where the etcd cluster cannot elect or maintain a leader.


## Use Case 3: Incident Diagnosis
Correlate API server failures or cluster instability with etcd leadership issues.


## Use Case 4: High Availability Validation
Verify that leader election mechanisms are functioning correctly in multi-node etcd clusters.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* etcd Documentation: https://etcd.io/docs/
* Prometheus Querying: https://prometheus.io/docs/prometheus/latest/querying/basics/
