### Example 1: Get an Event Hub Namespace Private Endpoint Connection
```powershell
Get-AzEventHubPrivateEndpointConnection -ResourceGroupName {resourceGroup} -NamespaceName {namespace} -Name 00000000000
```

```output
ConnectionState              : Approved
Description                  :
Id                           : /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.EventHub/namespaces/{namespace}/privateEndpointC
                               onnections/00000000000
Location                     : Australia East
Name                         : 00000000000
PrivateEndpointId            : /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.Network/privateEndpoints/{privateEndpointName}
ProvisioningState            : Succeeded
ResourceGroupName            : {resourceGroup}
```

Gets details of private endpoint connection `00000000000` created under EventHub namespace `myNamespace`.

### Example 2: List all private endpoint connections on an EventHub namespace
```powershell
Get-AzEventHubPrivateEndpointConnection -ResourceGroupName myResourceGroup -NamespaceName myNamespace
```

Lists all private endpoint connections of EventHub namespace `myNamespace`.