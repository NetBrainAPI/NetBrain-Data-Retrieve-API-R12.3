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
The <b>Container Resource Requests</b> API retrieves the resource requests configured for containers within a Kubernetes pod.

Resource requests define the minimum amount of CPU or memory guaranteed to a container. These values are used by the Kubernetes scheduler to determine pod placement and ensure resource availability.

This API helps in understanding how much resource is reserved for workloads and enables comparison with actual usage.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: kube_pod_container_resource_requests
* <b>Source</b>: kube-state-metrics
* <b>Metric Type</b>: Gauge
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Container Resource Requests

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
## PromQL Conceptual Expression (CPU Requests)
```
kube_pod_container_resource_requests{
  namespace="$NAME_SPACE",
  pod="$KUBNAME",
  resource="cpu"
}
```

## PromQL Conceptual Expression (Memory Requests)
```
kube_pod_container_resource_requests{
  namespace="$NAME_SPACE",
  pod="$KUBNAME",
  resource="memory"
}
```

## Optional Aggregation (Pod Level)
```
sum(
  kube_pod_container_resource_requests{
    namespace="$NAME_SPACE",
    pod="$KUBNAME"
  }
)
```


# Interpretation <a name="interpretation"></a>
* Higher value → More resources reserved for the container
* Lower value → Less guaranteed resource allocation


# Success Criteria <a name="success-criteria"></a>
The container resource requests are successfully retrieved and aligned with expected configuration.

# Alert Criteria <a name="alert-criteria"></a>
Not typically used as a direct alert. However, abnormal or misconfigured resource requests may lead to inefficient scheduling or resource fragmentation within the cluster.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Capacity Planning
Understand reserved resources across workloads.


## Use Case 2: Scheduling Optimization
Ensure resource requests align with actual usage.


## Use Case 3: Resource Right-Sizing
Compare requested resources with real consumption metrics.


## Use Case 4: Cluster Efficiency
Identify over-provisioned workloads consuming unnecessary reserved capacity.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* kube-state-metrics: https://github.com/kubernetes/kube-state-metrics
* Kubernetes Resource Management: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
