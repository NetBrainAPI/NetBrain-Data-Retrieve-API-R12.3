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
The <b>API Server Latency</b> API monitors the average time taken by the Kubernetes API server to process requests.

High API latency can indicate:

* Control plane overload
* Resource contention
* Network delays
* Inefficient workloads or excessive API calls

This API calculates the average latency per request using Prometheus metrics and evaluates whether it exceeds acceptable thresholds.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: apiserver_request_duration_seconds
* <b>Components Used</b>:
  * _sum → total latency
  * _count → total requests
* <b>Source</b>: Kubernetes API Server metrics
* <b>Metric Type</b>: Histogram (converted to average latency)
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: rate()
* <b>Display Name in NetBrain</b>: API Server Latency

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Rate Interval
Defines the time window used in rate calculation.

* Example: 1m, 5m, 10m
* Default: 5m


## Unit
Defines the output unit.

* Seconds (default)
* Milliseconds (optional conversion)



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the latency above which the API server is considered under performance stress.

* Example: 1 second
* Note: Threshold values should be tuned based on workload and SLA requirements.


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
* rate(v range-vector) (Primary)
* increase(v range-vector)


# Evaluation Logic <a name="evaluation-logic"></a>
## PromQL Conceptual Expression
```
rate(apiserver_request_duration_seconds_sum[<rate_interval>])
/
rate(apiserver_request_duration_seconds_count[<rate_interval>])
> <threshold>
```


# Interpretation <a name="interpretation"></a>
* Value below threshold → API server latency is within acceptable limits
* Value above threshold → API server is experiencing high latency


# Success Criteria <a name="success-criteria"></a>
The average API request latency has remained within the defined threshold at the time of evaluation.

# Alert Criteria <a name="alert-criteria"></a>
The average API request latency exceeds the defined threshold. This condition may indicate control plane overload, degraded performance, or increased request processing time, which can impact overall cluster responsiveness.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Control Plane Performance Monitoring
Track API responsiveness to ensure efficient cluster operations.


## Use Case 2: Detecting API Server Overload
Identify when the API server is under heavy load or resource pressure.


## Use Case 3: Latency Trend Analysis
Monitor changes in request latency over time using rate-based calculations.


## Use Case 4: Incident Correlation
Correlate increased latency with deployment spikes, scaling events, or system issues.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
