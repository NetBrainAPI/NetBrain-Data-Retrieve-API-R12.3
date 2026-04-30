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
The <b>Container Application Memory Usage</b> API monitors the active memory consumption of containers within a Kubernetes pod.

The metric container_memory_working_set_bytes represents the memory actively used by the container, excluding cached memory. This provides a more accurate indication of real memory pressure compared to total memory usage.

High memory usage may lead to:

* Container OOM (Out of Memory) termination
* Pod instability
* Node memory pressure

This API provides a real-time view of container memory utilization.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: container_memory_working_set_bytes
* <b>Source</b>: cAdvisor (via kubelet / Prometheus)
* <b>Metric Type</b>: Gauge (bytes)
* <b>Evaluation Type</b>: Instant query
* <b>Display Name in NetBrain</b>: Container Application Memory Usage

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Unit
Defines how the metric is displayed.

* bytes
* MB / GB



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines memory usage above which the container is considered under pressure.

Can be defined as:

* Absolute value (bytes)
* Percentage of container memory limit (recommended)


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
container_memory_working_set_bytes{
  namespace="$NAME_SPACE",
  pod="$KUBNAME",
  container!=""
}
```

## PromQL Conceptual Expression (Pod Level)
```
sum(
  container_memory_working_set_bytes{
    namespace="$NAME_SPACE",
    pod="$KUBNAME",
    container!=""
  }
)
```


# Interpretation <a name="interpretation"></a>
* Higher value → Increased active memory usage
* Lower value → Lower memory consumption


# Success Criteria <a name="success-criteria"></a>
The container memory usage is within the defined threshold at the time of evaluation.

# Alert Criteria <a name="alert-criteria"></a>
The container memory usage exceeds the defined threshold. This condition may lead to container restarts, memory pressure, or degraded application performance.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Memory Pressure Detection
Monitor active memory usage to prevent OOM conditions.


## Use Case 2: Application Performance Monitoring
Track real memory consumption excluding cache.


## Use Case 3: Resource Optimization
Compare actual usage with configured requests and limits.


## Use Case 4: Troubleshooting Instability
Identify containers consuming excessive memory.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* cAdvisor Metrics: https://github.com/google/cadvisor
* Prometheus Documentation: https://prometheus.io/docs/
