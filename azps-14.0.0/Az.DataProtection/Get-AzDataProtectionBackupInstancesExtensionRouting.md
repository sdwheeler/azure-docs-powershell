---
external help file: Az.DataProtection-help.xml
Module Name: Az.DataProtection
online version: https://learn.microsoft.com/powershell/module/az.dataprotection/get-azdataprotectionbackupinstancesextensionrouting
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DataProtection/DataProtection/help/Get-AzDataProtectionBackupInstancesExtensionRouting.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DataProtection/DataProtection/help/Get-AzDataProtectionBackupInstancesExtensionRouting.md
---

# Get-AzDataProtectionBackupInstancesExtensionRouting

## SYNOPSIS
Gets a list of backup instances associated with a tracked resource

## SYNTAX

```
Get-AzDataProtectionBackupInstancesExtensionRouting -ResourceId <String> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION
Gets a list of backup instances associated with a tracked resource

## EXAMPLES

### Example 1: Get backup instance extension routing
```powershell
$diskARMID = "subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx/resourceGroups/testRG/providers/Microsoft.Compute/disks/testDisk"
Get-AzDataProtectionBackupInstancesExtensionRouting -ResourceId $diskARMID
```

This command gets a list of backup instances associated with a tracked resource.
To execute the cmdlet, We pass the datasource ARM ID to the parameter ResourceId.

## PARAMETERS

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

### -ResourceId
ARM path of the resource to be protected using Microsoft.DataProtection

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DataProtection.Models.Api202501.IBackupInstanceResource

## NOTES

## RELATED LINKS
