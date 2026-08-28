# Table of Contents
- [Introduction](#introduction)
- [Content](#content)
- [Samples](#sample)

# Introduction <a name="introduction"></a>
Passing-in the keyword "route_table" for the param data_type, the API returns the the route tables of each circuit peering, which describes the currently advertised routes table associated with the express route circuit.

# Content <a name="content"></a>
Below are the Azure APIs used to generate this configuration.

|Resource/Action|Relationship|Azure API Version|Azure API document|
|------|------|------|------|
| Express Route Circuits - List Routes Table | self | 2023-09-01 | https://learn.microsoft.com/en-us/rest/api/expressroute/express-route-circuits/list-routes-table
| Express Route Circuits - Get | To get ExpressRoute Circuit peerings | 2023-09-01 | https://learn.microsoft.com/en-us/rest/api/expressroute/express-route-circuits/get

# Samples <a name="sample"></a>

<details>
<summary>API Response</summary>
<p>

```json
[
    {
        "peeringName": "AzurePrivatePeering",
        "peeringId": "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/expressRouteCircuits/curcuitName/peerings/AzurePrivatePeering",
        "routeTable": [
            {
                "network": "",
                "nextHop": "",
                "locPrf": "",
                "weight": 0,
                "path": ""
            }
        ]
    },
    {
        "peeringName": "MicrosoftPeering",
        "peeringId": "/subscriptions/subId/resourceGroups/rg/providers/Microsoft.Network/expressRouteCircuits/curcuitName/peerings/MicrosoftPeering",
        "routeTable": [
            {
                "network": "",
                "nextHop": "",
                "locPrf": "",
                "weight": 0,
                "path": ""
            }
        ]
    }
]

```
</p>
</details>