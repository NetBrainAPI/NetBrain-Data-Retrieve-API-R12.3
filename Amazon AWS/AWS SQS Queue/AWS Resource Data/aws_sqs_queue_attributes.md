# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get the details of Amazon SQS queue attributes.
The response includes information such as message retention period, visibility timeout, delivery delay, redrive policy, encryption settings, queue size metrics, and access control configurations.

The API belongs to the device type <b>AWS SQS</b> and uses the <b>sqs</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS SQS |
| AWS API Resource Type | sqs |
| AWS Rest API Function | get_queue_attributes |
| Filter key passed in API | QueueUrl |

You can find more information about the AWS Rest API get_queue_attributes here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs/client/get_queue_attributes.html