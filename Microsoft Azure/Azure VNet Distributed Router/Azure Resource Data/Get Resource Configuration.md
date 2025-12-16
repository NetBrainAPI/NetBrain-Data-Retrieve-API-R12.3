# Table of Contents
- [Introduction](#introduction)
- [Content](#content)
- [Samples](#sample)

# Introduction <a name="introduction"></a>
The configuration of the Azure virtual network distributed router relies solely on the corresponding Azure API of the virtual network. The Azure API provides detailed information regarding the configuration of the virtual network, including its connectivity, security, etc.

# Content <a name="content"></a>
Below are the Azure APIs used to generate this configuration.
|**Resource/Action**|**Relationship**|**Azure API Version**|**Azure API document**|
|------|------|------|------|
| Virtual Networks - Get | self | 2021-08-01 | https://learn.microsoft.com/en-us/rest/api/virtualnetwork/virtual-networks/get | 


# Samples <a name="sample"></a>
<details><summary>Configuration File</summary>

```json
{
  "netbrainNotes": "This config file is generated via API",
  "netbrainHostName": "test-vnet(<ResourceGroup>)(<Subscription_ID_Prefix>)(VirtualNetworkDistributedRouter)",
  "name": "test-vnet",
  "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet",
  "type": "Microsoft.Network/virtualNetworks",
  "location": "westus",
  "properties": {
    "provisioningState": "Succeeded",
    "addressSpace": {
      "addressPrefixes": [
        "10.0.0.0/16"
      ]
    },
    "subnets": [
      {
        "name": "subnet1",
        "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/subnet1",
        "properties": {
          "provisioningState": "Succeeded",
          "addressPrefix": "10.0.1.0/24",
          "ipConfigurations": [
            {
              "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe"
            }
          ]
        }
      }
    ],
    "virtualNetworkPeerings": [
      {
        "id": "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet1/virtualNetworkPeerings/peer2",
        "name": "peer",
        "properties": {
          "allowVirtualNetworkAccess": true,
          "allowForwardedTraffic": false,
          "allowGatewayTransit": false,
          "useRemoteGateways": false,
          "remoteVirtualNetwork": {
            "id": "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet3"
          },
          "remoteAddressSpace": {
            "addressPrefixes": [
              "13.0.0.0/8"
            ]
          },
          "remoteVirtualNetworkAddressSpace": {
            "addressPrefixes": [
              "13.0.0.0/8"
            ]
          },
          "remoteBgpCommunities": {
            "virtualNetworkCommunity": "12076:20003",
            "regionalCommunity": "12076:50004"
          },
          "peeringState": "Initiated",
          "peeringSyncLevel": "FullyInSync",
          "provisioningState": "Succeeded"
        }
      }
    ]
  }
}
```

</details>
<br />