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
The <b>Container Memory Resource Limits</b> API retrieves the configured memory limits for containers within a Kubernetes pod.

Memory limits define the maximum amount of memory a container can consume. If a container exceeds this limit, it may be terminated by the system (OOMKilled).

This API helps ensure that memory constraints are properly defined and enables comparison with actual memory usage for performance and stability analysis.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_resource_limits_memory_bytes
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Container Memory Resource Limits

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Unit
Defines how the metric is displayed.

* bytes
* MB / GB



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
## PromQL Conceptual Expression (Container Level)
```
kube_pod_container_resource_limits_memory_bytes{
  namespace="$NAME_SPACE",
  pod="$KUBNAME"
}
```

## PromQL Conceptual Expression (Pod Level)
```
sum(
  kube_pod_container_resource_limits_memory_bytes{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }
)
```


# Interpretation <a name="interpretation"></a>
* Higher value → Higher maximum allowed memory usage
* Lower value → More restrictive memory limit


# Success Criteria <a name="success-criteria"></a>
The container memory limits are successfully retrieved and aligned with expected configuration.

# Alert Criteria <a name="alert-criteria"></a>
Not typically used as a standalone alert. However:

* Missing memory limits → Risk of uncontrolled memory usage
* Very low limits → Risk of frequent OOM terminations
* Very high limits → Risk of node memory exhaustion


# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Memory Governance
Ensure containers have defined memory limits.


## Use Case 2: OOM Risk Prevention
Identify containers likely to exceed memory limits.


## Use Case 3: Resource Optimization
Compare memory limits with actual usage (working_set_bytes).


## Use Case 4: Capacity Planning
Understand maximum memory allocation across workloads.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
