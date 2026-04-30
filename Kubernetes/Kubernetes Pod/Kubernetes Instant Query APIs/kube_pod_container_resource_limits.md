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
The <b>Container Resource Limits</b> API retrieves the resource limits configured for containers within a Kubernetes pod.

Resource limits define the maximum amount of CPU or memory a container is allowed to consume. If a container exceeds its defined limits:

* CPU may be throttled
* Memory overuse may result in OOM (Out of Memory) termination

This API helps ensure that workloads are properly constrained and enables comparison between limits, requests, and actual usage.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_resource_limits
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Gauge
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Container Resource Limits

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Resource Type
Defines the resource to evaluate.

* cpu
* memory


## Unit
* <b>CPU</b>: cores
* <b>Memory</b>: bytes / MB / GB



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


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression (CPU Limits)
```
kube_pod_container_resource_limits{
  namespace="$NAME_SPACE",
  pod="$KUBNAME",
  resource="cpu"
}
```

## PromQL Conceptual Expression (Memory Limits)
```
kube_pod_container_resource_limits{
  namespace="$NAME_SPACE",
  pod="$KUBNAME",
  resource="memory"
}
```

## Optional Aggregation (Pod Level)
```
sum(
  kube_pod_container_resource_limits{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }
)
```


# Interpretation <a name="interpretation"></a>
* Higher value → Higher maximum allowed resource usage
* Lower value → More restrictive resource limits


# Success Criteria <a name="success-criteria"></a>
The container resource limits are successfully retrieved and aligned with expected configuration.

# Alert Criteria <a name="alert-criteria"></a>
Not typically used as a standalone alert. However:

* Missing limits → Risk of uncontrolled resource usage
* Extremely high limits → Risk of node resource exhaustion
* Very low limits → Risk of throttling or OOM


# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Resource Governance
Ensure containers have proper limits defined.


## Use Case 2: Preventing Resource Exhaustion
Avoid containers consuming excessive CPU or memory.


## Use Case 3: OOM Risk Analysis
Identify containers with limits too close to actual usage.


## Use Case 4: Optimization
Compare:

* Requests vs Limits vs Actual Usage



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
* Kubernetes Resource Management: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
