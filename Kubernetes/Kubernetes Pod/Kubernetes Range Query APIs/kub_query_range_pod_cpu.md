# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Aggregation Function](#aggregation-function)
- [Evaluation Logic](#evaluation-logic)
- [Interpretation](#interpretation)
- [Success Criteria](#success-criteria)
- [Alert Criteria](#alert-criteria)
- [Use Case Examples](#use-case-examples)
- [Reference](#reference)


# Overview <a name="overview"></a>
The <b>Pod CPU Utilization (Range)</b> API monitors CPU usage of containers within a Kubernetes pod over a defined time range.

CPU usage is calculated as the rate of CPU time consumed by containers and aggregated at the pod level. This provides a time-averaged view of CPU utilization and helps detect sustained CPU pressure.

High CPU utilization over time may indicate:

* Resource-intensive workloads
* Inefficient application behavior
* CPU contention on nodes


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: container_cpu_usage_seconds_total
* <b>Source</b>: cAdvisor (via kubelet / Prometheus)
* <b>Metric Type</b>: Counter (converted using rate())
* <b>Evaluation Type</b>: Time-series aggregation
* <b>Base Function</b>: rate()
* <b>Default Aggregation</b>: avg_over_time
* <b>Display Name in NetBrain</b>: Container Range Pod CPU

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Namespace
Defines the Kubernetes namespace.


## Pod Name
Defines the target pod.


## Time Range
Defines how far back to evaluate CPU usage.

* Example: 5m, 15m, 1h
* Default: 5m


## Rate Interval
Defines the window used inside the rate() function.

* Example: 1m, 2m, 5m
* Default: 2m


## Unit
* CPU cores



# Aggregation Function <a name="aggregation-function"></a>
## Default (Recommended)
* avg_over_time(v range-vector)

## Threshold
Defines CPU usage above which the pod is considered under high load.

* Example: environment-specific


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
avg_over_time(
  sum(
    rate(container_cpu_usage_seconds_total{
      namespace="$NAME_SPACE",
      pod="$KUBNAME",
      container!=""
    }[<rate_interval>])
  )[<time_range>:]
) > <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → CPU usage is within acceptable limits
* Value above threshold → Pod is under sustained CPU pressure


# Success Criteria <a name="success-criteria"></a>
The CPU utilization of the pod has remained within the defined threshold over the evaluated time range.

# Alert Criteria <a name="alert-criteria"></a>
The CPU utilization of the pod has exceeded the defined threshold over the evaluated time range. This condition may indicate sustained workload pressure or inefficient resource usage.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Sustained CPU Pressure Detection
Identify pods consistently consuming high CPU.


## Use Case 2: Performance Monitoring
Track CPU trends over time for applications.


## Use Case 3: Resource Optimization
Detect inefficient CPU usage patterns.


## Use Case 4: Capacity Planning
Use historical CPU trends for scaling decisions.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* cAdvisor Metrics: https://github.com/google/cadvisor
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
