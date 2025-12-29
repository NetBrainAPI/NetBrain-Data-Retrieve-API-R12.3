# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to list all rules configured for an AWS VPC Lattice service listener.
The response includes rule priorities, match conditions, action definitions, default rule identification, and configuration details that determine how requests are routed to service targets.

The API belongs to the device type <b>AWS VPC Lattice</b> and uses the <b>vpc-lattice</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS VPC Lattice |
| AWS API Resource Type | vpc-lattice |
| AWS Rest API Function | list_rules |
| Filter key passed in API | listenerIdentifier, serviceIdentifier |

You can find more information about the AWS Rest API <b>list_rules</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/vpclattice/client/list_rules.html
