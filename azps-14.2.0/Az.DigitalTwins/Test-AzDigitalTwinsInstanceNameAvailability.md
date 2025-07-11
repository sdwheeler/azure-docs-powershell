---
external help file: Az.DigitalTwins-help.xml
Module Name: Az.DigitalTwins
online version: https://learn.microsoft.com/powershell/module/az.digitaltwins/test-azdigitaltwinsinstancenameavailability
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DigitalTwins/DigitalTwins/help/Test-AzDigitalTwinsInstanceNameAvailability.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DigitalTwins/DigitalTwins/help/Test-AzDigitalTwinsInstanceNameAvailability.md
---

# Test-AzDigitalTwinsInstanceNameAvailability

## SYNOPSIS
Check if a DigitalTwinsInstance name is available.

## SYNTAX

### CheckExpanded (Default)
```
Test-AzDigitalTwinsInstanceNameAvailability -Location <String> [-SubscriptionId <String>] -Name <String>
 [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CheckViaJsonString
```
Test-AzDigitalTwinsInstanceNameAvailability -Location <String> [-SubscriptionId <String>] -JsonString <String>
 [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CheckViaJsonFilePath
```
Test-AzDigitalTwinsInstanceNameAvailability -Location <String> [-SubscriptionId <String>]
 -JsonFilePath <String> [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CheckViaIdentityExpanded
```
Test-AzDigitalTwinsInstanceNameAvailability -InputObject <IDigitalTwinsIdentity> -Name <String>
 [-DefaultProfile <PSObject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Check if a DigitalTwinsInstance name is available.

## EXAMPLES

### Example 1: Check if a DigitalTwinsInstance name is available.
```powershell
Test-AzDigitalTwinsInstanceNameAvailability -Location westus2 -Name testName
```

```output
Message                  NameAvailable Reason
-------                  ------------- ------
'testName' is available.          True
```

Check if a DigitalTwinsInstance name is available.

### Example 2: Check if a DigitalTwinsInstance name is not available.
```powershell
Test-AzDigitalTwinsInstanceNameAvailability -Location westus2 -Name !testName
```

```output
Message                                                                                                                                NameAvailable Reason
-------                                                                                                                                ------------- ------
'!testName' must be between 3 and 63 characters. Alphanumerics and hyphens are allowed. Value must start and end with an alphanumeric.         False Invalid
```

Check if a DigitalTwinsInstance name is not available.

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

### -InputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.DigitalTwins.Models.IDigitalTwinsIdentity
Parameter Sets: CheckViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JsonFilePath
Path of Json file supplied to the Check operation

```yaml
Type: System.String
Parameter Sets: CheckViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JsonString
Json string supplied to the Check operation

```yaml
Type: System.String
Parameter Sets: CheckViaJsonString
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Location
Location of DigitalTwinsInstance.

```yaml
Type: System.String
Parameter Sets: CheckExpanded, CheckViaJsonString, CheckViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Resource name.

```yaml
Type: System.String
Parameter Sets: CheckExpanded, CheckViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The subscription identifier.

```yaml
Type: System.String
Parameter Sets: CheckExpanded, CheckViaJsonString, CheckViaJsonFilePath
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

### Microsoft.Azure.PowerShell.Cmdlets.DigitalTwins.Models.IDigitalTwinsIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.DigitalTwins.Models.ICheckNameResult

## NOTES

## RELATED LINKS
