---
external help file: Az.Purview-help.xml
Module Name: Az.Purview
online version: https://learn.microsoft.com/powershell/module/Az.Purview/new-azpurviewazuresynapseworkspacedatasourceobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewAzureSynapseWorkspaceDataSourceObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Purview/Purview/help/New-AzPurviewAzureSynapseWorkspaceDataSourceObject.md
---

# New-AzPurviewAzureSynapseWorkspaceDataSourceObject

## SYNOPSIS
Create an in-memory object for AzureSynapseWorkspaceDataSource.

## SYNTAX

```
New-AzPurviewAzureSynapseWorkspaceDataSourceObject [-CollectionReferenceName <String>]
 [-CollectionType <String>] [-DedicatedSqlEndpoint <String>] [-Location <String>] [-ResourceGroup <String>]
 [-ResourceName <String>] [-ServerlessSqlEndpoint <String>] [-SubscriptionId <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for AzureSynapseWorkspaceDataSource.

## EXAMPLES

### Example 1: Create Azure Synapse workspace data source object
```powershell
New-AzPurviewAzureSynapseWorkspaceDataSourceObject -CollectionReferenceName 'parv-brs-2' -CollectionType 'CollectionReference' -DedicatedSqlEndpoint 'g1euap.sql.azuresynapse.net' -ServerlessSqlEndpoint 'rg1euap-ondemand.sql.azuresynapse.net'
```

```output
CollectionLastModifiedAt :
CollectionReferenceName  : parv-brs-2
CollectionType           : CollectionReference
CreatedAt                :
DedicatedSqlEndpoint     : g1euap.sql.azuresynapse.net
Id                       :
Kind                     : AzureSynapseWorkspace
LastModifiedAt           :
Location                 :
Name                     :
ResourceGroup            :
ResourceName             :
Scan                     :
ServerlessSqlEndpoint    : rg1euap-ondemand.sql.azuresynapse.net
SubscriptionId           :
```

Create Azure Synapse workspace data source object

## PARAMETERS

### -CollectionReferenceName

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

### -CollectionType

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

### -DedicatedSqlEndpoint

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

### -Location

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

### -ResourceGroup

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

### -ResourceName

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

### -ServerlessSqlEndpoint

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Purviewdata.Models.AzureSynapseWorkspaceDataSource

## NOTES

## RELATED LINKS
