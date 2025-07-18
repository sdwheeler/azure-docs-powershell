---
external help file: Microsoft.Azure.PowerShell.Cmdlets.RecoveryServices.Backup.dll-Help.xml
Module Name: Az.RecoveryServices
online version: https://learn.microsoft.com/powershell/module/az.recoveryservices/set-azrecoveryservicesresourceguardmapping
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/RecoveryServices/RecoveryServices/help/Set-AzRecoveryServicesResourceGuardMapping.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/RecoveryServices/RecoveryServices/help/Set-AzRecoveryServicesResourceGuardMapping.md
---

# Set-AzRecoveryServicesResourceGuardMapping

## SYNOPSIS
Sets the resource guard mapping to the recovery services vault.

## SYNTAX

```
Set-AzRecoveryServicesResourceGuardMapping [-VaultId <String>] [-DefaultProfile <IAzureContextContainer>]
 -ResourceGuardId <String> [-Token <String>] [-SecureToken <SecureString>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Sets the resource guard mapping to the recovery services vault. This cmdlet creates a mapping between the RS vault and Resource guard, after this cmdlet is run, sensitive operations are protected by the resource guard as per MUA.

## EXAMPLES

### Example 1 Create a resource guard mapping in a cross tenant scenario

```powershell
$token = (Get-AzAccessToken -TenantId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx").Token
Set-AzRecoveryServicesResourceGuardMapping -VaultId $vault.ID -ResourceGuardId "Resource-Guard-Id" -Token $token
```

The first command fetches the access token for the resource guard tenant where the resource guard is present. The second command creates a mapping between the RSVault $vault and Resource guard. Please note that token parameter is optional and only needed to authenticate cross tenant protected operations.

## PARAMETERS

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

### -ResourceGuardId
ResourceGuardId of the ResourceGuard to be mapped with RecoveryServicesVault

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

### -SecureToken
Parameter to authorize operations protected by cross tenant resource guard. Use command (Get-AzAccessToken -TenantId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx").Token to fetch authorization token for different tenant

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Token
Auxiliary access token for authenticating critical operation to resource guard subscription

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

### -VaultId
ARM ID of the Recovery Services Vault.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
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

### System.String

## OUTPUTS

### Microsoft.Azure.Management.RecoveryServices.Backup.Models.ResourceGuardProxyBaseResource

## NOTES

## RELATED LINKS
