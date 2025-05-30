---
external help file: Az.Cdn-help.xml
Module Name: Az.Cdn
online version: https://learn.microsoft.com/powershell/module/Az.Cdn/new-azfrontdoorcdnmigrationwebapplicationfirewallmappingobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/New-AzFrontDoorCdnMigrationWebApplicationFirewallMappingObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/New-AzFrontDoorCdnMigrationWebApplicationFirewallMappingObject.md
---

# New-AzFrontDoorCdnMigrationWebApplicationFirewallMappingObject

## SYNOPSIS
Create an in-memory object for MigrationWebApplicationFirewallMapping.

## SYNTAX

```
New-AzFrontDoorCdnMigrationWebApplicationFirewallMappingObject [-MigratedFromId <String>]
 [-MigratedToId <String>] [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for MigrationWebApplicationFirewallMapping.

## EXAMPLES

### Example 1: Create an in-memory object for MigrationWebApplicationFirewallMapping
```powershell
New-AzFrontDoorCdnMigrationWebApplicationFirewallMappingObject -MigratedFromId migrateFromId -MigratedToId migrateToId
```

```output
MigratedFromId MigratedToId
-------------- ------------
migrateFromId  migrateToId
```

Create an in-memory object for MigrationWebApplicationFirewallMapping

## PARAMETERS

### -MigratedFromId
Resource ID.

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

### -MigratedToId
Resource ID.

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

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.MigrationWebApplicationFirewallMapping

## NOTES

## RELATED LINKS
