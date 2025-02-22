---
external help file:
Module Name: Az.EventHub
online version: https://docs.microsoft.com/powershell/module/az.eventhub/set-azeventhub
schema: 2.0.0
---

# Set-AzEventHub

## SYNOPSIS
Updates an EventHub Entity

## SYNTAX

### SetExpanded (Default)
```
Set-AzEventHub -Name <String> -NamespaceName <String> -ResourceGroupName <String> [-SubscriptionId <String>]
 [-ArchiveNameFormat <String>] [-BlobContainer <String>] [-CaptureEnabled] [-DestinationName <String>]
 [-Encoding <EncodingCaptureDescription>] [-IntervalInSeconds <Int32>] [-MessageRetentionInDays <Int64>]
 [-SizeLimitInBytes <Int32>] [-SkipEmptyArchive] [-Status <EntityStatus>] [-StorageAccountResourceId <String>]
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-Confirm] [-WhatIf] [<CommonParameters>]
```

### SetViaIdentityExpanded
```
Set-AzEventHub -InputObject <IEventHubIdentity> [-ArchiveNameFormat <String>] [-BlobContainer <String>]
 [-CaptureEnabled] [-DestinationName <String>] [-Encoding <EncodingCaptureDescription>]
 [-IntervalInSeconds <Int32>] [-MessageRetentionInDays <Int64>] [-SizeLimitInBytes <Int32>]
 [-SkipEmptyArchive] [-Status <EntityStatus>] [-StorageAccountResourceId <String>]
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-Confirm] [-WhatIf] [<CommonParameters>]
```

## DESCRIPTION
Updates an EventHub Entity

## EXAMPLES

### Example 1: Set capture on an existing EventHub entity
```powershell
Set-AzEventHub -Name myEventHub -ResourceGroupName myResourceGroup -NamespaceName myNamespace -ArchiveNameFormat "{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}" -BlobContainer container -CaptureEnabled -DestinationName EventHubArchive.AzureBlockBlob -Encoding Avro -IntervalInSeconds 600 -SizeLimitInBytes 11000000 -SkipEmptyArchive -StorageAccountResourceId "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount"
```

```output
ArchiveNameFormat            : {Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}
BlobContainer                : container
CaptureEnabled               : true
CreatedAt                    : 9/1/2022 5:55:46 AM
DataLakeAccountName          :
DataLakeFolderPath           :
DataLakeSubscriptionId       :
DestinationName              :
Encoding                     : Avro
Id                           : /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.EventHub/namespaces/myNamespace/eventhubs/myFirstEventHub
IntervalInSeconds            : 600
Location                     : centralus
MessageRetentionInDays       : 6
Name                         : myFirstEventHub
PartitionCount               : 5
PartitionId                  : {0}
ResourceGroupName            : myResourceGroup
SizeLimitInBytes             : 11000000
SkipEmptyArchive             : true
Status                       : Active
```

Updates EventHub entity `myEventHub` from namespace `myNamespace` to enable capture on it.

### Example 2: Update EventHub EventHub entity using InputObject parameter set
```powershell
$eventhub = Get-AzEventHub -Name myEventHub -ResourceGroupName myResourceGroup -NamespaceName myNamespace
Set-AzEventHub -InputObject $eventhub -MessageRetentionInDays 3
```

```output
ArchiveNameFormat            : {Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}
BlobContainer                : container
CaptureEnabled               : true
CreatedAt                    : 9/1/2022 5:55:46 AM
DataLakeAccountName          :
DataLakeFolderPath           :
DataLakeSubscriptionId       :
DestinationName              :
Encoding                     : Avro
Id                           : /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.EventHub/namespaces/myNamespace/eventhubs/myFirstEventHub
IntervalInSeconds            : 600
Location                     : centralus
MessageRetentionInDays       : 6
Name                         : myFirstEventHub
PartitionCount               : 5
PartitionId                  : {0}
ResourceGroupName            : myResourceGroup
SizeLimitInBytes             : 11000000
SkipEmptyArchive             : true
Status                       : Active
```

Updates `MessageRetentionInDays` in EventHub entity `myEventHub` to 3 days.

## PARAMETERS

### -ArchiveNameFormat
Blob naming convention for archive, e.g.
{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}.
Here all the parameters (Namespace,EventHub ..
etc) are mandatory irrespective of order

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
Run the command as a job

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BlobContainer
Blob container Name

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaptureEnabled
A value that indicates whether capture description is enabled.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with Azure.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases: AzureRMContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DestinationName
Name for capture destination

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding
Enumerates the possible values for the encoding format of capture description.
Note: 'AvroDeflate' will be deprecated in New API Version

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.EventHub.Support.EncodingCaptureDescription
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Identity parameter.
To construct, see NOTES section for INPUTOBJECT properties and create a hash table.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.EventHub.Models.IEventHubIdentity
Parameter Sets: SetViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IntervalInSeconds
The time window allows you to set the frequency with which the capture to Azure Blobs will happen, value should between 60 to 900 seconds

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageRetentionInDays
Number of days to retain the events for this Event Hub, value should be 1 to 7 days

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The name of EventHub Entity.

```yaml
Type: System.String
Parameter Sets: SetExpanded
Aliases: EventHubName

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NamespaceName
The name of EventHub namespace.

```yaml
Type: System.String
Parameter Sets: SetExpanded
Aliases: Namespace

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoWait
Run the command asynchronously

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceGroupName
The name of the resource group.
The name is case insensitive.

```yaml
Type: System.String
Parameter Sets: SetExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SizeLimitInBytes
The size window defines the amount of data built up in your Event Hub before an capture operation, value should be between 10485760 to 524288000 bytes

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipEmptyArchive
A value that indicates whether to Skip Empty Archives

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status
Enumerates the possible values for the status of the Event Hub.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.EventHub.Support.EntityStatus
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StorageAccountResourceId
Resource id of the storage account to be used to create the blobs

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.

```yaml
Type: System.String
Parameter Sets: SetExpanded
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.PowerShell.Cmdlets.EventHub.Models.IEventHubIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.EventHub.Models.Api202201Preview.IEventhub

## NOTES

ALIASES

COMPLEX PARAMETER PROPERTIES

To create the parameters described below, construct a hash table containing the appropriate properties. For information on hash tables, run Get-Help about_Hash_Tables.


`INPUTOBJECT <IEventHubIdentity>`: Identity parameter.
  - `[Alias <String>]`: The Disaster Recovery configuration name
  - `[ApplicationGroupName <String>]`: The Application Group name 
  - `[AuthorizationRuleName <String>]`: The authorization rule name.
  - `[ClusterName <String>]`: The name of the Event Hubs Cluster.
  - `[ConsumerGroupName <String>]`: The consumer group name
  - `[EventHubName <String>]`: The Event Hub name
  - `[Id <String>]`: Resource identity path
  - `[NamespaceName <String>]`: The Namespace name
  - `[PrivateEndpointConnectionName <String>]`: The PrivateEndpointConnection name
  - `[ResourceAssociationName <String>]`: The ResourceAssociation Name
  - `[ResourceGroupName <String>]`: Name of the resource group within the azure subscription.
  - `[SchemaGroupName <String>]`: The Schema Group name 
  - `[SubscriptionId <String>]`: Subscription credentials that uniquely identify a Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

## RELATED LINKS

