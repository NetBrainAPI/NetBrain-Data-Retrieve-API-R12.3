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
The <b>API Server Request Rate</b> API monitors the number of requests processed by the Kubernetes API server over time.

The metric apiserver_request_duration_seconds_count represents the total number of API requests handled. By applying a rate function, this API provides insight into request throughput and load on the control plane.

High request rates may indicate:

* Increased cluster activity
* Excessive API usage
* Potential control plane saturation

This API is also a key component in calculating average API latency when combined with latency sum metrics.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: apiserver_request_duration_seconds_count
* <b>Source</b>: Kubernetes API Server metrics
* <b>Metric Type</b>: Counter
* <b>Evaluation Type</b>: Instant query with range function
* <b>Base Function</b>: rate()
* <b>Display Name in NetBrain</b>: Server Number of Requests

# User-Defined Parameters <a name="user-defined-parameters"></a>
## Rate Interval
Defines the time window used to calculate request rate.

* Example: 1m, 5m, 10m
* Default: 5m


## Unit
Defines how the result is interpreted.

* Requests per second



# Aggregation Function <a name="aggregation-function"></a>
## Threshold
Defines the request rate above which the API server may be considered under heavy load.

* Example: environment-specific
* Note: Threshold values depend on cluster size and workload patterns.


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
sum(
  rate(apiserver_request_duration_seconds_count[<rate_interval>])
)
```


# Interpretation <a name="interpretation"></a>
* Higher value → Increased API request throughput
* Lower value → Reduced API activity


# Success Criteria <a name="success-criteria"></a>
The API request rate is within expected operational limits for the cluster.

# Alert Criteria <a name="alert-criteria"></a>
The API request rate exceeds the expected threshold, indicating potential control plane overload or excessive API usage, which may impact performance and responsiveness.

# Use Case Examples <a name="use-case-examples"></a>
## Use Case 1: Control Plane Load Monitoring
Track how heavily the API server is being utilized.


## Use Case 2: Detecting Traffic Spikes
Identify sudden increases in API activity.


## Use Case 3: Supporting Latency Analysis
Use alongside latency metrics to determine if high latency is caused by increased request volume.


## Use Case 4: Capacity Planning
Understand API usage trends to scale control plane resources.



# Reference <a name="reference"></a>
* Kubernetes Documentation: https://kubernetes.io/docs/
* Kubernetes Metrics Reference: https://kubernetes.io/docs/reference/instrumentation/metrics/
* Prometheus Query Functions: https://prometheus.io/docs/prometheus/latest/querying/functions/
