---
external help file: Az.Cdn-help.xml
Module Name: Az.Cdn
online version: https://learn.microsoft.com/powershell/module/Az.Cdn/new-azfrontdoorcdnprofilelogscrubbingobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/New-AzFrontDoorCdnProfileLogScrubbingObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/New-AzFrontDoorCdnProfileLogScrubbingObject.md
---

# New-AzFrontDoorCdnProfileLogScrubbingObject

## SYNOPSIS
Create an in-memory object for ProfileLogScrubbing.

## SYNTAX

```
New-AzFrontDoorCdnProfileLogScrubbingObject [-ScrubbingRule <IProfileScrubbingRules[]>] [-State <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for ProfileLogScrubbing.

## EXAMPLES

### Example 1: Create an in-memory object for ProfileUpgradeParameters, for two LogScrubbingRules
```powershell
$scrubbingRule1 = New-AzFrontDoorCdnProfileScrubbingRulesObject -MatchVariable RequestIPAddress -State Enabled
$scrubbingRule2 = New-AzFrontDoorCdnProfileScrubbingRulesObject -MatchVariable RequestUri -State Enabled
New-AzFrontDoorCdnProfileLogScrubbingObject -ScrubbingRule @($scrubbingRule1, $scrubbingRule2) -State Enabled
```

```output
State
-----
Enabled
```

Create an in-memory object for ProfileUpgradeParameters, for two LogScrubbingRules

## PARAMETERS

### -ScrubbingRule
List of log scrubbing rules applied to the Azure Front Door profile logs.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.IProfileScrubbingRules[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -State
State of the log scrubbing config.
Default value is Enabled.

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

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ProfileLogScrubbing

## NOTES

## RELATED LINKS
