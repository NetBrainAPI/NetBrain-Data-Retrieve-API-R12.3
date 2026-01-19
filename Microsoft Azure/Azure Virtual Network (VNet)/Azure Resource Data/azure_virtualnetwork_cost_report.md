# Table of Contents
- [Introduction](#introduction)


# Introduction <a name="introduction"></a>
The API is used to get the Azure Virtual Network cost information for the specified URL from Azure API Server (https://management.azure.com/).



Once the report generation operation completes, the polling endpoint will provide a 200 response along with details on the report blob(s) that are available for download. The details on the file(s) available for download will be available in the polling response body.



For a complete list of available API resources for Azure Cost Management, please refer to Microsoft document: https://learn.microsoft.com/en-us/rest/api/cost-management/?view=rest-cost-management-2023-11-01

For the original Azure API detailed information, please refer to Microsoft document: https://learn.microsoft.com/en-us/rest/api/cost-management/generate-cost-details-report/create-operation?view=rest-cost-management-2023-11-01&tabs=HTTP