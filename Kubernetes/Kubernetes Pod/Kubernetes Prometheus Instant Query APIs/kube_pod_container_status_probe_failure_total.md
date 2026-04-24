# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Aggregation Function](#aggregation-function)
- [Supported Functions](#supported-functions)
- [Interpretation](#interpretation)
- [Success Criteria](#success-criteria)
- [Alert Criteria](#alert-criteria)
- [Use Case Examples](#use-case-examples)
- [Reference](#reference)


# Overview <a name="overview"></a>
The <b>Liveness & Readiness Probe Failures</b> API monitors failures in container health checks within a Kubernetes pod.

Kubernetes uses probes to determine container health:

## Liveness Probe
* Verifies if a container is functioning correctly
* Failure triggers container restart

## Readiness Probe
* Determines if a container is ready to accept traffic
* Failure removes the pod from service endpoints

Frequent probe failures may indicate:

* Application instability
* Resource constraints
* Dependency failures (e.g., database connectivity)
* Misconfigured health checks


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_status_probe_failure_total
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Counter
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: increase()
* <b>Display Name in NetBrain</b>: Container Status Probe Failure

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Probe Type
Defines which probe to evaluate.

* liveness
* readiness


## Rate Interval
Defines the time window to evaluate failures.

* Example: 5m, 10m
* Default: 5m



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines number of failures indicating an issue.

* Example: `> 3` failures in 5 minutes
* Note: Should be tuned based on application behavior


# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* count(v)
* max(v)
* topk(k, v)

## Range Functions (Used Internally)
* increase(v range-vector) (Primary)
* rate(v range-vector)


# Interpretation <a name="interpretation"></a>
* Low or zero failures → Container health checks are stable
* Increasing failures → Potential application or infrastructure issues


# Success Criteria <a name="success-criteria"></a>
The number of liveness and readiness probe failures remains within the defined threshold over the evaluated interval.

# Alert Criteria <a name="alert-criteria"></a>
The number of probe failures exceeds the defined threshold within the evaluated interval. This condition may indicate application instability, resource constraints, or dependency failures affecting container health.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Application Health Monitoring
Detect containers failing health checks.


## Use Case 2: Crash Detection
Identify repeated liveness failures causing restarts.


## Use Case 3: Traffic Routing Issues
Detect readiness failures preventing traffic routing.


## Use Case 4: Performance Bottleneck Detection
Correlate probe failures with latency or backend issues.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
