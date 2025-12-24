# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get detailed information about an Amazon EC2 Auto Scaling Group (ASG).
The response includes configuration details such as desired capacity, minimum and maximum size, instance health status, scaling policies, launch templates, availability zones, and lifecycle states of associated EC2 instances.

The API belongs to the device type <b>AWS Auto Scaling</b> and uses the <b>autoscaling</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS Auto Scaling |
| AWS API Resource Type | autoscaling |
| AWS Rest API Function | describe_auto_scaling_groups |
| Filter key passed in API | AutoScalingGroupNames |

You can find more information about the AWS Rest API <b>describe_auto_scaling_groups</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/autoscaling/client/describe_auto_scaling_groups.html
