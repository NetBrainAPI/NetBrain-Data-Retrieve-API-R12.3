# Table of Contents
- [Overview](#overview)
- [Metric Info](#metric-info)
- [User-Defined Parameters](#user-defined-parameters)
- [Use Cases Example](#example)
    - [Use Case 1 -- Monitoring API Performance](#example-1) 
    - [Use Case 2 -- Identifying Backend Bottlenecks](#example-2)
- [Reference](#reference)

# Overview <a name="overview"></a>
The <b>API Gateway Latency</b> metric measures the total time (in milliseconds) between when API Gateway receives a request and when it returns a response to the client. This includes both the integration latency (backend processing time) and the time API Gateway itself spends processing the request.

Monitoring this metric is essential for understanding end-to-end API performance, identifying bottlenecks, and ensuring a responsive user experience.


# Metric Info <a name="metric-info"></a>
* <b>Metric Name</b>: Latency
* <b>Namespace</b>: AWS/ApiGateway
* <b>Unit / Stat</b>: SampleCount
* <b>Display Name in NetBrain</b>: API Gateway Latency

# User-Defined Parameters <a name="user-defined-parameters"></a>
* <b>Start Time / End Time</b>: Defines the time window for which latency data points are retrieved. Useful for performance monitoring, trend analysis, and debugging slow responses.
* <b>Default</b>: Last 24 hours
* <b>Statistics</b>: Default value is Count.
  * <b>Average</b>: Shows the typical end-to-end response time for API calls..
  * <b>Sum</b>: Represents total cumulative latency across all requests.
  * <b>Minimum</b>: Identifies the fastest response times, useful for baseline performance.
  * <b>Maximum</b>: Shows peak latency during spikes or backend slowdowns.
* <b>Period</b>: Default value is 3600 second.
  * <b>Recommended Values</b>:
    * <b>60 seconds</b> for real-time latency monitoring.
    * <b>300 seconds</b> for general operational visibility.
    * <b>3600 seconds</b> for long-term latency trend analysis.

# Use Cases Example <a name="example"></a>
## Use Case 1: Monitoring API Performance <a name="example-1"></a>
Track the <b>Latency</b> metric to measure how quickly your API handles requests end-to-end. High latency may point to backend slowness, increased load, or API Gateway processing delays.


## Use Case 2: Identifying Backend Bottlenecks <a name="example-2"></a>
When API latency increases, comparing it with <b>IntegrationLatency</b> helps determine whether delays occur inside API Gateway or within the backend. This supports rapid root-cause analysis during slow API events.



# Reference <a name="reference"></a>
* <b>Metrics Details</b>: AWS APIGateway Data In Metric Documentation
https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-metrics-and-dimensions.html
* <b>AWS CloudWatch Parameters</b>: AWS Boto3 CloudWatch GetMetricData Documentation
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch/client/get_metric_data.html