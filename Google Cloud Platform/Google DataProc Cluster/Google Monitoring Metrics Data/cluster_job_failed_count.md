# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Reference](#reference)

# Overview <a name="overview"></a>
The API is used to indicates the number of jobs that have failed on a cluster.

It leverages GCP Cloud Monitoring to fetch metrics of GCP resources via the GCP RESTful API. 



# Metric Info <a name="metric-info"></a>
* <b>Resource Label Used</b>: Name of the DataProc Cluster (cluster_name)
* <b>GCP Original Name</b>: cluster/job/failed_count


# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Define the time range to analyze data points, useful for historical analysis or recent monitoring. Default time range is the last 24 hours.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: https://cloud.google.com/monitoring/api/metrics_gcp
* <b>Monitoring API</b>: https://cloud.google.com/monitoring/api/v3/filters