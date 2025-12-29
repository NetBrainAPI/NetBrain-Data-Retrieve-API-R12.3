# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get detailed execution history for a workflow run in Amazon Simple Workflow Service (SWF).
The response includes workflow events such as activity scheduling, task execution results, state transitions, failures, timeouts, and completion information, providing full visibility into the workflow lifecycle.

The API belongs to the device type <b>AWS SWF</b> and uses the <b>swf</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS SWF |
| AWS API Resource Type | swf |
| AWS Rest API Function | get_workflow_execution_history |
| Filter key passed in API | domain, execution |

You can find more information about the AWS Rest API get_workflow_execution_history here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/swf/client/get_workflow_execution_history.html

