# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get the details of listeners associated with an AWS Global Accelerator accelerator.
The response includes listener configuration such as port ranges, protocols, client affinity settings, associated endpoint groups, and listener operational status.

The API belongs to the device type <b>AWS Global Accelerator</b> and uses the <b>globalaccelerator</b> resource type of the AWS REST API.

# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS Global Accelerator |
| AWS API Resource Type | globalaccelerator |
| AWS Rest API Function | list_listeners |
| Filter key passed in API | acceleratorArn |

You can find more information about the AWS Rest API <b>list_listeners</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/globalaccelerator/client/list_listeners.html