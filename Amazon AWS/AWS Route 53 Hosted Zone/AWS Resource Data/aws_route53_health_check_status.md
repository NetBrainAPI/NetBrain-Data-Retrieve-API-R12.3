# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to retrieve and check the overall health status of all Route 53 health checks associated with a hosted zone.
The response includes information such as health check states, failure reasons, IP addresses probed, request status, and endpoint availability information.

The API belongs to the device type <b>AWS Route 53</b> and uses the <b>route53</b> resource type of the AWS REST API.
# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS Route 53 |
| AWS API Resource Type | route53 |
| AWS Rest API Function | get_health_check_status |
| Filter key passed in API | healthCheckId |

You can find more information about the AWS Rest API <b>get_health_check_status</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/route53/client/get_health_check_status.html