# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get the details of Amazon ECS services running within a cluster.
The response includes information such as desired and running task counts, deployment state, load balancer configuration, service scheduling strategy, network settings, and overall service configuration.

The API belongs to the device type <b>AWS ECS</b> and uses the <b>ecs</b> resource type of the AWS REST API.
# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS ECS |
| AWS API Resource Type | ecs |
| AWS Rest API Function | describe_services |
| Filter key passed in API | <i>None</i> |

You can find more information about the AWS Rest API <b>describe_services</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/ecs/client/describe_services.html