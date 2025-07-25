---
external help file: Az.NeonPostgres-help.xml
Module Name: Az.NeonPostgres
online version: https://learn.microsoft.com/powershell/module/az.neonpostgres/get-azneonpostgresneonrole
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/NeonPostgres/NeonPostgres/help/Get-AzNeonPostgresNeonRole.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/NeonPostgres/NeonPostgres/help/Get-AzNeonPostgresNeonRole.md
---

# Get-AzNeonPostgresNeonRole

## SYNOPSIS
List NeonRole resources by Branch

## SYNTAX

```
Get-AzNeonPostgresNeonRole -BranchName <String> -OrganizationName <String> -ProjectName <String>
 -ResourceGroupName <String> [-SubscriptionId <String[]>] [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION
List NeonRole resources by Branch

## EXAMPLES

### Example 1: List all roles and permissions associated with a specific branch
```powershell
Get-AzNeonPostgresNeonRole -BranchName "br-damp-bird-a82olmcu" -ProjectName "dawn-breeze-86932056" -OrganizationName "NeonDemoOrgPS1" -ResourceGroupName "neonrg" -SubscriptionId "00000000-0000-0000-0000-000000000000"
```

```output
Attribute                    : 
BranchId                     : br-damp-bird-a82olmcu
CreatedAt                    : May 12, 2025 8:02 AM
EntityId                     : 
EntityName                   : neondb_owner
Id                           : 
IsSuperUser                  : False
Name                         : 
Permission                   : 
ProvisioningState            : Succeeded
SystemDataCreatedAt          : 
SystemDataCreatedBy          : 
SystemDataCreatedByType      : 
SystemDataLastModifiedAt     : 
SystemDataLastModifiedBy     : 
SystemDataLastModifiedByType : 
Type                         :
```

List all roles and permissions associated with a specific branch

## PARAMETERS

### -BranchName
The name of the Branch

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultProfile
The DefaultProfile parameter is not functional.
Use the SubscriptionId parameter when available if executing the cmdlet against a different subscription.

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

### -OrganizationName
Name of the Neon Organizations resource

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectName
The name of the Project

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
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
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.
The value must be an UUID.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.NeonPostgres.Models.INeonRole

## NOTES

## RELATED LINKS
