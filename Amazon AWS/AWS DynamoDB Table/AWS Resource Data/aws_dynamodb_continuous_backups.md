# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get the details of continuous backups for an Amazon DynamoDB table.
The response includes information such as point-in-time recovery (PITR) status, last enabled time, and backup configuration applied to the table.

The API belongs to the device type <b>AWS DynamoDB</b> and uses the <b>dynamodb</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS DynamoDB |
| AWS API Resource Type | dynamodb |
| AWS Rest API Function | describe_continuous_backups |
| Filter key passed in API | <i>None</i> |

You can find more information about the AWS Rest API <b>describe_continuous_backups</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb/client/describe_continuous_backups.html