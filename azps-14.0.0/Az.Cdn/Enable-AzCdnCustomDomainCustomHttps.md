---
external help file: Az.Cdn-help.xml
Module Name: Az.Cdn
online version: https://learn.microsoft.com/powershell/module/az.cdn/enable-azcdncustomdomaincustomhttps
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/Enable-AzCdnCustomDomainCustomHttps.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/Enable-AzCdnCustomDomainCustomHttps.md
---

# Enable-AzCdnCustomDomainCustomHttps

## SYNOPSIS
Enable https delivery of the custom domain.

## SYNTAX

### EnableViaIdentity (Default)
```
Enable-AzCdnCustomDomainCustomHttps -InputObject <ICdnIdentity>
 -CustomDomainHttpsParameter <ICustomDomainHttpsParameters> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### EnableViaJsonString
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointName <String> -ProfileName <String>
 -ResourceGroupName <String> [-SubscriptionId <String>] -JsonString <String> [-DefaultProfile <PSObject>]
 [-AsJob] [-NoWait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### EnableViaJsonFilePath
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointName <String> -ProfileName <String>
 -ResourceGroupName <String> [-SubscriptionId <String>] -JsonFilePath <String> [-DefaultProfile <PSObject>]
 [-AsJob] [-NoWait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### EnableViaIdentityProfileExpanded
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointName <String>
 -ProfileInputObject <ICdnIdentity> [-CertificateSource <String>] [-MinimumTlsVersion <String>]
 [-ProtocolType <String>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### EnableViaIdentityProfile
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointName <String>
 -ProfileInputObject <ICdnIdentity> -CustomDomainHttpsParameter <ICustomDomainHttpsParameters>
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### EnableViaIdentityEndpointExpanded
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointInputObject <ICdnIdentity>
 [-CertificateSource <String>] [-MinimumTlsVersion <String>] [-ProtocolType <String>]
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### EnableViaIdentityEndpoint
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointInputObject <ICdnIdentity>
 -CustomDomainHttpsParameter <ICustomDomainHttpsParameters> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Enable
```
Enable-AzCdnCustomDomainCustomHttps -CustomDomainName <String> -EndpointName <String> -ProfileName <String>
 -ResourceGroupName <String> [-SubscriptionId <String>]
 -CustomDomainHttpsParameter <ICustomDomainHttpsParameters> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Enable https delivery of the custom domain.

## EXAMPLES

### Example 1: Enable an AzureCDN custom domain under the AzureCDN endpoint
```powershell
$customDomainHttpsParameter = New-AzCdnManagedHttpsParametersObject -CertificateSourceParameterCertificateType Dedicated -CertificateSource Cdn  -ProtocolType ServerNameIndication
Enable-AzCdnCustomDomainCustomHttps -ResourceGroupName testps-rg-da16jm -ProfileName cdn001 -EndpointName endptest001 -CustomDomainName customdomain001 -CustomDomainHttpsParameter $customDomainHttpsParameter
```

```output
Name            ResourceGroupName
----            -----------------
customdomain001 testps-rg-da16jm
```

Enable an AzureCDN custom domain under the AzureCDN endpoint

## PARAMETERS

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

### -CertificateSource
Defines the source of the SSL certificate.

```yaml
Type: System.String
Parameter Sets: EnableViaIdentityProfileExpanded, EnableViaIdentityEndpointExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CustomDomainHttpsParameter
The JSON object that contains the properties to secure a custom domain.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICustomDomainHttpsParameters
Parameter Sets: EnableViaIdentity, EnableViaIdentityProfile, EnableViaIdentityEndpoint, Enable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CustomDomainName
Name of the custom domain within an endpoint.

```yaml
Type: System.String
Parameter Sets: EnableViaJsonString, EnableViaJsonFilePath, EnableViaIdentityProfileExpanded, EnableViaIdentityProfile, EnableViaIdentityEndpointExpanded, EnableViaIdentityEndpoint, Enable
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

### -EndpointInputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICdnIdentity
Parameter Sets: EnableViaIdentityEndpointExpanded, EnableViaIdentityEndpoint
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -EndpointName
Name of the endpoint under the profile which is unique globally.

```yaml
Type: System.String
Parameter Sets: EnableViaJsonString, EnableViaJsonFilePath, EnableViaIdentityProfileExpanded, EnableViaIdentityProfile, Enable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICdnIdentity
Parameter Sets: EnableViaIdentity
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JsonFilePath
Path of Json file supplied to the Enable operation

```yaml
Type: System.String
Parameter Sets: EnableViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JsonString
Json string supplied to the Enable operation

```yaml
Type: System.String
Parameter Sets: EnableViaJsonString
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumTlsVersion
TLS protocol version that will be used for Https

```yaml
Type: System.String
Parameter Sets: EnableViaIdentityProfileExpanded, EnableViaIdentityEndpointExpanded
Aliases:

Required: False
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

### -ProfileInputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICdnIdentity
Parameter Sets: EnableViaIdentityProfileExpanded, EnableViaIdentityProfile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ProfileName
Name of the CDN profile which is unique within the resource group.

```yaml
Type: System.String
Parameter Sets: EnableViaJsonString, EnableViaJsonFilePath, Enable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProtocolType
Defines the TLS extension protocol that is used for secure delivery.

```yaml
Type: System.String
Parameter Sets: EnableViaIdentityProfileExpanded, EnableViaIdentityEndpointExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceGroupName
Name of the Resource group within the Azure subscription.

```yaml
Type: System.String
Parameter Sets: EnableViaJsonString, EnableViaJsonFilePath, Enable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
Azure Subscription ID.

```yaml
Type: System.String
Parameter Sets: EnableViaJsonString, EnableViaJsonFilePath, Enable
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

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICdnIdentity

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICustomDomainHttpsParameters

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICustomDomain

## NOTES

## RELATED LINKS
