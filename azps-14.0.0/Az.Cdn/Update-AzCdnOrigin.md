---
external help file: Az.Cdn-help.xml
Module Name: Az.Cdn
online version: https://learn.microsoft.com/powershell/module/az.cdn/update-azcdnorigin
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/Update-AzCdnOrigin.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Cdn/Cdn/help/Update-AzCdnOrigin.md
---

# Update-AzCdnOrigin

## SYNOPSIS
update an existing origin within an endpoint.

## SYNTAX

### UpdateExpanded (Default)
```
Update-AzCdnOrigin -EndpointName <String> -Name <String> -ProfileName <String> -ResourceGroupName <String>
 [-SubscriptionId <String>] [-Enabled] [-HostName <String>] [-HttpPort <Int32>] [-HttpsPort <Int32>]
 [-OriginHostHeader <String>] [-Priority <Int32>] [-PrivateLinkAlias <String>]
 [-PrivateLinkApprovalMessage <String>] [-PrivateLinkLocation <String>] [-PrivateLinkResourceId <String>]
 [-Weight <Int32>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaJsonString
```
Update-AzCdnOrigin -EndpointName <String> -Name <String> -ProfileName <String> -ResourceGroupName <String>
 [-SubscriptionId <String>] -JsonString <String> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaJsonFilePath
```
Update-AzCdnOrigin -EndpointName <String> -Name <String> -ProfileName <String> -ResourceGroupName <String>
 [-SubscriptionId <String>] -JsonFilePath <String> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaIdentityProfileExpanded
```
Update-AzCdnOrigin -EndpointName <String> -Name <String> -ProfileInputObject <ICdnIdentity> [-Enabled]
 [-HostName <String>] [-HttpPort <Int32>] [-HttpsPort <Int32>] [-OriginHostHeader <String>] [-Priority <Int32>]
 [-PrivateLinkAlias <String>] [-PrivateLinkApprovalMessage <String>] [-PrivateLinkLocation <String>]
 [-PrivateLinkResourceId <String>] [-Weight <Int32>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaIdentityProfile
```
Update-AzCdnOrigin -EndpointName <String> -Name <String> -ProfileInputObject <ICdnIdentity>
 -OriginUpdateProperty <IOriginUpdateParameters> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaIdentityEndpointExpanded
```
Update-AzCdnOrigin -Name <String> -EndpointInputObject <ICdnIdentity> [-Enabled] [-HostName <String>]
 [-HttpPort <Int32>] [-HttpsPort <Int32>] [-OriginHostHeader <String>] [-Priority <Int32>]
 [-PrivateLinkAlias <String>] [-PrivateLinkApprovalMessage <String>] [-PrivateLinkLocation <String>]
 [-PrivateLinkResourceId <String>] [-Weight <Int32>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaIdentityEndpoint
```
Update-AzCdnOrigin -Name <String> -EndpointInputObject <ICdnIdentity>
 -OriginUpdateProperty <IOriginUpdateParameters> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UpdateViaIdentityExpanded
```
Update-AzCdnOrigin -InputObject <ICdnIdentity> [-Enabled] [-HostName <String>] [-HttpPort <Int32>]
 [-HttpsPort <Int32>] [-OriginHostHeader <String>] [-Priority <Int32>] [-PrivateLinkAlias <String>]
 [-PrivateLinkApprovalMessage <String>] [-PrivateLinkLocation <String>] [-PrivateLinkResourceId <String>]
 [-Weight <Int32>] [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
update an existing origin within an endpoint.

## EXAMPLES

### Example 1: Update an AzureCDN origin under the AzureCDN endpoint
```powershell
Update-AzCdnOrigin -ResourceGroupName testps-rg-da16jm -ProfileName cdn001 -EndpointName endptest001 -Name origin1 -HttpPort 456 -HttpsPort 789
```

```output
Name    ResourceGroupName
----    -----------------
origin1 testps-rg-da16jm
```

Update an AzureCDN origin under the AzureCDN endpoint

### Example 2: Update an AzureCDN origin under the AzureCDN endpoint via identity
```powershell
Get-AzCdnOrigin -ResourceGroupName testps-rg-da16jm -ProfileName cdn001 -EndpointName endptest001 -Name origin1 | Update-AzCdnOrigin -HttpPort 456 -HttpsPort 789
```

```output
Name    ResourceGroupName
----    -----------------
origin1 testps-rg-da16jm
```

Update an AzureCDN origin under the AzureCDN endpoint via identity

### Example 3: Update an AzureCDN origin under the AzureCDN endpoint, disable the origin
```powershell
Update-AzCdnOrigin -ResourceGroupName testps-rg-da16jm -ProfileName cdn001 -EndpointName endptest001 -Name origin1 -HttpPort 456 -HttpsPort 789
```

```output
Name    ResourceGroupName
----    -----------------
origin1 testps-rg-da16jm
```

Update an AzureCDN origin under the AzureCDN endpoint, disable the origin

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

### -Enabled
Origin is enabled for load balancing or not

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

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
Parameter Sets: UpdateViaIdentityEndpointExpanded, UpdateViaIdentityEndpoint
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
Parameter Sets: UpdateExpanded, UpdateViaJsonString, UpdateViaJsonFilePath, UpdateViaIdentityProfileExpanded, UpdateViaIdentityProfile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName
The address of the origin.
Domain names, IPv4 addresses, and IPv6 addresses are supported.This should be unique across all origins in an endpoint.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HttpPort
The value of the HTTP port.
Must be between 1 and 65535.

```yaml
Type: System.Int32
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HttpsPort
The value of the HTTPS port.
Must be between 1 and 65535.

```yaml
Type: System.Int32
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICdnIdentity
Parameter Sets: UpdateViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JsonFilePath
Path of Json file supplied to the Update operation

```yaml
Type: System.String
Parameter Sets: UpdateViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JsonString
Json string supplied to the Update operation

```yaml
Type: System.String
Parameter Sets: UpdateViaJsonString
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Name of the origin which is unique within the endpoint.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaJsonString, UpdateViaJsonFilePath, UpdateViaIdentityProfileExpanded, UpdateViaIdentityProfile, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityEndpoint
Aliases: OriginName

Required: True
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

### -OriginHostHeader
The host header value sent to the origin with each request.
If you leave this blank, the request hostname determines this value.
Azure CDN origins, such as Web Apps, Blob Storage, and Cloud Services require this host header value to match the origin hostname by default.
This overrides the host header defined at Endpoint

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OriginUpdateProperty
Origin properties needed for origin update.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.IOriginUpdateParameters
Parameter Sets: UpdateViaIdentityProfile, UpdateViaIdentityEndpoint
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Priority
Priority of origin in given origin group for load balancing.
Higher priorities will not be used for load balancing if any lower priority origin is healthy.Must be between 1 and 5

```yaml
Type: System.Int32
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateLinkAlias
The Alias of the Private Link resource.
Populating this optional field indicates that this origin is 'Private'

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateLinkApprovalMessage
A custom message to be included in the approval request to connect to the Private Link.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateLinkLocation
The location of the Private Link resource.
Required only if 'privateLinkResourceId' is populated

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateLinkResourceId
The Resource Id of the Private Link resource.
Populating this optional field indicates that this backend is 'Private'

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
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
Parameter Sets: UpdateViaIdentityProfileExpanded, UpdateViaIdentityProfile
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
Parameter Sets: UpdateExpanded, UpdateViaJsonString, UpdateViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceGroupName
Name of the Resource group within the Azure subscription.

```yaml
Type: System.String
Parameter Sets: UpdateExpanded, UpdateViaJsonString, UpdateViaJsonFilePath
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
Parameter Sets: UpdateExpanded, UpdateViaJsonString, UpdateViaJsonFilePath
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### -Weight
Weight of the origin in given origin group for load balancing.
Must be between 1 and 1000

```yaml
Type: System.Int32
Parameter Sets: UpdateExpanded, UpdateViaIdentityProfileExpanded, UpdateViaIdentityEndpointExpanded, UpdateViaIdentityExpanded
Aliases:

Required: False
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

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.ICdnIdentity

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.IOriginUpdateParameters

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Cdn.Models.IOrigin

## NOTES

## RELATED LINKS
