---
external help file: Az.Migrate-help.xml
Module Name: Az.Migrate
online version: https://learn.microsoft.com/powershell/module/az.migrate/new-azmigratenicmapping
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Migrate/Migrate/help/New-AzMigrateNicMapping.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Migrate/Migrate/help/New-AzMigrateNicMapping.md
---

# New-AzMigrateNicMapping

## SYNOPSIS
Creates an object to update NIC properties of a replicating server.

## SYNTAX

```
New-AzMigrateNicMapping -NicID <String> [-TargetNicSelectionType <String>] [-TargetNicSubnet <String>]
 [-TargetNicName <String>] [-TargetNicIP <String>] [-TestNicSubnet <String>] [-TestNicIP <String>]
 [<CommonParameters>]
```

## DESCRIPTION
The New-AzMigrateNicMapping cmdlet creates a mapping of the source NIC attached to the server to be migrated.
This object is provided as an input to the Set-AzMigrateServerReplication cmdlet to update the NIC and its properties for a replicating server.

## EXAMPLES

### Example 1: Create a NIC object
```powershell
New-AzMigrateNicMapping -NicID a2399354-653a-464e-a567-d30ef5467a31 -TargetNicSelectionType primary -TargetNicIP "172.17.1.17"
```

```output
IsPrimaryNic IsSelectedForMigration NicId                                TargetStaticIPAddress TargetSubnetName
------------ ---------------------- -----                                --------------------- ----------------
false        false                  a2399354-653a-464e-a567-d30ef5467a31
```

Creates a NIC update object.

## PARAMETERS

### -NicID
Specifies the ID of the NIC to be updated.

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

### -TargetNicIP
Specifies the IP within the destination subnet to be used for the NIC.

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

### -TargetNicName
Specifies the name of the NIC to be created.

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

### -TargetNicSelectionType
Specifies whether the NIC to be updated will be the primary, secondary or not migrated.

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

### -TargetNicSubnet
Specifies the Subnet name for the NIC in the destination Virtual Network to which the server needs to be migrated.

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

### -TestNicIP
Specifies the IP within the destination test subnet to be used for the NIC.

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

### -TestNicSubnet
Specifies the Subnet name for the NIC in the destination Virtual Network to which the server needs to be test migrated.

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

### Microsoft.Azure.PowerShell.Cmdlets.Migrate.Models.Api202401.IVMwareCbtNicInput

## NOTES

## RELATED LINKS
