---
external help file: Microsoft.Azure.PowerShell.Cmdlets.CosmosDB.dll-Help.xml
Module Name: Az.CosmosDB
online version: https://learn.microsoft.com/powershell/module/az.cosmosdb/update-azcosmosdbaccountregion
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/CosmosDB/CosmosDB/help/Update-AzCosmosDBAccountRegion.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/CosmosDB/CosmosDB/help/Update-AzCosmosDBAccountRegion.md
---

# Update-AzCosmosDBAccountRegion

## SYNOPSIS
Update Regions of a Cosmos DB Account.

## SYNTAX

### ByNameParameterSet (Default)
```
Update-AzCosmosDBAccountRegion -ResourceGroupName <String> -Name <String> [-Location <String[]>]
 [-LocationObject <PSLocation[]>] [-AsJob] [-DefaultProfile <IAzureContextContainer>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByResourceIdParameterSet
```
Update-AzCosmosDBAccountRegion [-Location <String[]>] [-LocationObject <PSLocation[]>] -ResourceId <String>
 [-AsJob] [-DefaultProfile <IAzureContextContainer>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObjectParameterSet
```
Update-AzCosmosDBAccountRegion [-Location <String[]>] [-LocationObject <PSLocation[]>]
 -InputObject <PSDatabaseAccountGetResults> [-AsJob] [-DefaultProfile <IAzureContextContainer>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Update Regions of a Cosmos DB Account. Location can be provided either as an object of type PSLocation or as strings of Location Name ordered by failover priority.
LocationObject parameter expects the list of current locations (failover priorities included) appended by the new LocationObjects corresponding to new locations to be added.
Location parameter expects the list of current location(ordered by failover priority) and the new locations. 
Please note, we only support Addition of Regions. Please provide either Location or LocationObject.

## EXAMPLES

### Example 1
```powershell
Update-AzCosmosDBAccountRegion -ResourceGroupName rg -Name dbname -Location "location1", "location2"
```

```output
Id                            : /subscriptions/{subscriptionid}/resourceGroups/rg/providers/Microsoft.DocumentDB/databaseAccounts/dbname
Name                          : dbname
Location                      : location1
Tags                          : {}
EnableCassandraConnector      :
EnableMultipleWriteLocations  : True
VirtualNetworkRules           : {}
FailoverPolicies              : {dbname-location1, dbname-location2}
Locations                     : {dbname-location1, dbname-location2}
ReadLocations                 : {dbname-location1, dbname-location2}
WriteLocations                : {dbname-location1}
Capabilities                  : {}
ConsistencyPolicy             : Microsoft.Azure.Management.CosmosDB.Fluent.Models.ConsistencyPolicy
EnableAutomaticFailover       : False
IsVirtualNetworkFilterEnabled : False
IpRules                       : {}
DatabaseAccountOfferType      : Standard
DocumentEndpoint              : https://dbname.documents.azure.com:443/
ProvisioningState             : Succeeded
Kind                          : GlobalDocumentDB
```

## PARAMETERS

### -AsJob
Run cmdlet in the background

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
Type: Microsoft.Azure.Commands.Common.Authentication.Abstractions.Core.IAzureContextContainer
Parameter Sets: (All)
Aliases: AzContext, AzureRmContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
ResourceId of the resource.

```yaml
Type: Microsoft.Azure.Commands.CosmosDB.Models.PSDatabaseAccountGetResults
Parameter Sets: ByObjectParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Location
Name of the location to be added.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LocationObject
Add a location to the Cosmos DB database account. Array of PSLocation objects.

```yaml
Type: Microsoft.Azure.Commands.CosmosDB.Models.PSLocation[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Name of the Cosmos DB database account.

```yaml
Type: System.String
Parameter Sets: ByNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceGroupName
Name of resource group.

```yaml
Type: System.String
Parameter Sets: ByNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceId
ResourceId of the resource.

```yaml
Type: System.String
Parameter Sets: ByResourceIdParameterSet
Aliases:

Required: True
Position: Named
Default value: None
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

### Microsoft.Azure.Commands.CosmosDB.Models.PSDatabaseAccount

## OUTPUTS

### Microsoft.Azure.Commands.CosmosDB.Models.PSDatabaseAccount

## NOTES

## RELATED LINKS
