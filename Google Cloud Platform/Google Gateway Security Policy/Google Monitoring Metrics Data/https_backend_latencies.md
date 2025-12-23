# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Reference](#reference)

# Overview <a name="overview"></a>
The API is used to retrieve the latency from the time when the request is sent by the proxy to the backend, to the time when the proxy receives the last byte of the response.

It leverages the GCP Cloud monitoring to fetch metrics of GCP resources via the GCP RESTful API.
# Metric Info <a name="metric-info"></a>
* <b>Resource Label Used</b>: Name of the Gateway (gateway_name)
* <b>GCP Original Name</b>: https/backend_latencies


# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Define the time range to analyze data points, useful for historical analysis or recent monitoring. Default time range is the last 24 hours.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: https://cloud.google.com/monitoring/api/metrics_gcp
* <b>Monitoring API</b>: https://cloud.google.com/monitoring/api/v3/filters