# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Supported Functions](#supported-functions)
- [Evaluation Logic](#evaluation-logic)
- [Interpretation](#interpretation)
- [Success Criteria](#success-criteria)
- [Alert Criteria](#alert-criteria)
- [Use Case Examples](#use-case-examples)
- [Reference](#reference)


# Overview <a name="overview"></a>
The <b>Container Waiting Reason</b> API identifies why a container within a Kubernetes pod is in a waiting state.

When a container is not running, Kubernetes provides a reason indicating the cause of the delay. This API retrieves those reasons using Prometheus metrics to help diagnose issues such as:

* Image pull failures
* Crash loops
* Initialization delays
* Configuration errors

This API provides real-time visibility into container startup and runtime issues.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_status_waiting_reason
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Gauge (label-based state indicator)
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Container Waiting Reason

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Reason (Optional Filter)
Defines specific waiting reasons to monitor.

Examples:

* CrashLoopBackOff
* ImagePullBackOff
* ErrImagePull
* ContainerCreating


## Unit
* Binary (0 or 1)



# Supported Functions <a name="supported-functions"></a>
## Instant Vector Aggregations
* sum(v)
* avg(v)
* min(v)
* max(v)
* count(v)
* topk(k, v)
* bottomk(k, v)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
kube_pod_container_status_waiting_reason{
  namespace="$NAME_SPACE",
  pod="$KUBNAME"
} == 1
```


# Interpretation <a name="interpretation"></a>
* Value = 1 → Container is in waiting state for the given reason
* Value = 0 → Condition not active


# Success Criteria <a name="success-criteria"></a>
No containers in the pod are in a waiting state due to critical failure reasons.

# Alert Criteria <a name="alert-criteria"></a>
One or more containers in the pod are in a waiting state due to failure conditions such as CrashLoopBackOff, ImagePullBackOff, or ErrImagePull. This indicates that the application is not running as expected.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Crash Detection
Identify containers stuck in CrashLoopBackOff.


## Use Case 2: Image Pull Failures
Detect issues pulling container images from registries.


## Use Case 3: Deployment Troubleshooting
Quickly identify why pods are not starting.


## Use Case 4: Runtime Stability Monitoring
Detect containers repeatedly failing to initialize.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
