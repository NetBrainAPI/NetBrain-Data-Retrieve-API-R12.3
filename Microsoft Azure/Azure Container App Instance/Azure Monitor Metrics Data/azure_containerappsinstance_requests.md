# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Reference](#reference)

# Overview <a name="overview"></a>
The API is used to retrieve Azure Container App Instance <b>Requests</b> metric data from Azure API Server (https://management.azure.com/). The metric is the requests processed. The Unit is Count. The Aggregation Types are Average, Total (Sum), Maximum and Minimum. Time Grain (Intervals at which the metric is sampled) is PT1M(Every 1 minute). The Azure monitor metrics original name: Requests.

It leverages the Azure Monitor solution to fetch metrics of Azure resources via the Azure RESTful API.

# Metric Info <a name="metric-info"></a>
* <b>Azure REST API Name</b>: Requests
* <b>NetBrain Display Name</b>: Requests
* <b>Unit</b>: Count

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Define the time range to analyze data points, useful for historical analysis or recent monitoring. Default time range is the last 24 hours.
* <b>Aggregation</b>: The process of taking multiple input values and then using them to produce a single output value via the rules defined by the aggregation type. For example, taking an average of multiple values. Valid values: Average, Total (Sum), Maximum and Minimum. Default value is <b>Average</b>.
  * <b>Average</b>: The average of the metric values captured over the aggregation interval. For most metrics, this value is Sum/Count.
* <b>Interval</b>: Valid values: PT1M. Default value is <b>PT1M</b>.
  * <b>PT1M</b>: Reporting interval for Metrics will have a timegrain of 1 minute.
* <b>Auto Adjust Timegrain</b>: When set to true, if the timespan passed in is not supported by this metric, the API will return the result using the closest supported timespan. When set to false, an error is returned for invalid timespan parameters. Defaults to <b>false</b>.
* <b>Validate Dimensions</b>: When set to false, invalid filter parameter values will be ignored. When set to true, an error is returned for invalid filter parameters. Defaults to <b>true</b>.
* <b>Top</b>: The maximum number of records to retrieve per resource ID in the request. Valid only if filter is specified. Defaults to <b>10</b>.


# Reference <a name="reference"></a>
* <b>Metrics Details</b>: https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-app-containerapps-metrics
* <b>Metrics API</b>: https://learn.microsoft.com/en-us/rest/api/monitor/metrics/list?view=rest-monitor-2023-10-01&tabs=HTTP
* <b>Supported Metrics</b>: https://learn.microsoft.com/en-us/azure/azure-monitor/reference/metrics-index