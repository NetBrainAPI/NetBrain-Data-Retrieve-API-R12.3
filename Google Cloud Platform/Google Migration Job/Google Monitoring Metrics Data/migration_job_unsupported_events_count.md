# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Reference](#reference)

# Overview <a name="overview"></a>
The API is used to retrieve the number of unsupported events per migration and per table. 

It leverages the GCP Cloud monitoring to fetch metrics of GCP resources via the GCP RESTful API.
# Metric Info <a name="metric-info"></a>
* <b>Resource Label Used</b>: ID of the Migration Job (migration_job_id)
* <b>GCP Original Name</b>: migration_job/unsupported_events_count


# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Define the time range to analyze data points, useful for historical analysis or recent monitoring. Default time range is the last 24 hours.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: https://cloud.google.com/monitoring/api/metrics_gcp
* <b>Monitoring API</b>: https://cloud.google.com/monitoring/api/v3/filters