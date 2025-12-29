# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to list and retrieve the details of tables in Amazon Keyspaces (for Apache Cassandra).
The response includes table configuration such as schema definitions, capacity mode, read/write throughput settings, encryption details, default TTL, and replication configurations.

The API belongs to the device type <b>AWS Keyspaces</b> and uses the <b>keyspaces</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS Keyspaces |
| AWS API Resource Type | keyspaces |
| AWS Rest API Function | get_table |
| Filter key passed in API | <i>None</i> |

You can find more information about the AWS Rest API <b>get_table</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/keyspaces/client/get_table.html