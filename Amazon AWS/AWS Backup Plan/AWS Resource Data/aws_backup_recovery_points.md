# Table of Contents
- [Introduction](#introduction)
- [Content](#content)


# Introduction <a name="introduction"></a>
The API is used to get the details of all Backup recovery points associated with AWS Backup.
The response includes information such as resource type, status, backup size, creation time, encryption settings, and lifecycle details for each recovery point.

The API belongs to the device type <b>AWS Backup</b> and uses the <b>backup</b> resource type of the AWS REST API.
# Content <a name="content"></a>
|||
|------|------|
| AWS Device Type | AWS Backup |
| AWS API Resource Type | backup |
| AWS Rest API Function | list_recovery_points_by_backup_vault |
| Filter key passed in API | backupVaultName |

You can find more information about the AWS Rest API <b>list_recovery_points_by_backup_vault</b> here
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/backup/client/list_recovery_points_by_backup_vault.html