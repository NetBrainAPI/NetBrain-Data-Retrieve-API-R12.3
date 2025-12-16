# Table of Contents
- [Introduction](#introduction)


# Introduction <a name="introduction"></a>
The API is used to get the Azure Virtual Network disk information from Azure API Server (https://management.azure.com/). The response includes the details like diskSizeGB, diskIOPSReadWrite, diskMBpsReadWrite, encryption, diskState, diskSizeBytes, publicIPs ect.



The original Azure RESTful API used is <Disks - Get; Public IP Addresses - Get>. 



For a complete list of available API resources for Azure Disks, please refer to Microsoft document: https://learn.microsoft.com/en-us/rest/api/compute/disks?view=rest-compute-2024-03-01

For a complete list of available API resources for Azure Public IP Addresses, please refer to Microsoft document: https://learn.microsoft.com/en-us/rest/api/virtualnetwork/public-ip-addresses?view=rest-virtualnetwork-2023-09-01

For the original Azure API detailed information, please refer to Microsoft document: 

* https://learn.microsoft.com/en-us/rest/api/compute/disks/get?view=rest-compute-2024-03-01&tabs=HTTP
* https://learn.microsoft.com/en-us/rest/api/virtualnetwork/public-ip-