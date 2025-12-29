# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to list all targets registered to an AWS VPC Lattice service target group.
The response includes details such as target health status, target identifiers, port configuration, availability, and any associated health check information.

The API belongs to the device type <b>AWS VPC Lattice</b> and uses the <b>vpc-lattice</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS VPC Lattice |
| AWS API Resource Type | vpc-lattice |
| AWS Rest API Function | list_targets |
| Filter key passed in API | targetGroupIdentifier |

You can find more information about the AWS Rest API <b>list_targets</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/vpclattice/client/list_targets.html