# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Reference](#reference)

# Overview <a name="overview"></a>
The API is used to retrieve the latency distribution (in milliseconds) in BigQuery Write API frontend, from receiving an AppendRowsRequest to sending an AppendRowsResponse.

It leverages GCP Cloud Monitoring to fetch metrics of GCP resources via the GCP RESTful API.

# Metric Info <a name="metric-info"></a>
* <b>Resource Label Used</b>: ID of the Module (module_id)
* <b>GCP Original Name</b>: dataflow_write/server_side_latencies 

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Define the time range to analyze data points, useful for historical analysis or recent monitoring. Default time range is the last 24 hours.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: https://cloud.google.com/monitoring/api/metrics_gcp
* <b>Monitoring API</b>: https://cloud.google.com/monitoring/api/v3/filters