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
The <b>Container Restart Count</b> API monitors the number of restarts for containers within a Kubernetes pod.

Container restarts typically indicate application or infrastructure issues such as:

* Application crashes
* OOM (Out of Memory) events
* Liveness probe failures
* Dependency failures

Tracking restart frequency over time helps identify unstable workloads and recurring failures.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_status_restarts_total
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Counter
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: increase()
* <b>Display Name in NetBrain</b>: Container Status Restarts

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Rate Interval
Defines the time window to evaluate restarts.

* Example: 5m, 10m, 15m
* Default: 5m



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines number of restarts indicating instability.

* Example: `> 2` restarts in 5 minutes
* Note: Should be tuned based on application tolerance


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* count(v)
* max(v)
* topk(k, v)

## Range Functions (Used Internally)
* increase(v range-vector) (Primary)
* rate(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression (Container Level)
```
increase(
  kube_pod_container_status_restarts_total{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }[<rate_interval>]
) > <threshold>
```

## PromQL Conceptual Expression (Pod Level)
```
sum(
  increase(
    kube_pod_container_status_restarts_total{
      namespace="$NAME_SPACE",
      pod="$KUBNAME"
    }[<rate_interval>]
  )
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Low or zero restarts → Stable container behavior
* Increasing restarts → Application or infrastructure issues


# Success Criteria <a name="success-criteria"></a>
The number of container restarts remains within the defined threshold over the evaluated interval.

# Alert Criteria <a name="alert-criteria"></a>
The number of container restarts exceeds the defined threshold within the evaluated interval. This condition may indicate application instability, resource exhaustion, or failing health checks.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: CrashLoop Detection
Identify containers repeatedly crashing and restarting.


## Use Case 2: Application Stability Monitoring
Track stability of workloads over time.


## Use Case 3: Resource Issue Detection
Correlate restarts with CPU/memory pressure or OOM events.


## Use Case 4: Deployment Validation
Ensure newly deployed pods are stable after rollout.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
