---
external help file: Az.ProviderHub-help.xml
Module Name: Az.ProviderHub
online version: https://learn.microsoft.com/powershell/module/az.providerhub/get-azproviderhubresourcetyperegistration
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/ProviderHub/ProviderHub/help/Get-AzProviderHubResourceTypeRegistration.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/ProviderHub/ProviderHub/help/Get-AzProviderHubResourceTypeRegistration.md
---

# Get-AzProviderHubResourceTypeRegistration

## SYNOPSIS
Gets a resource type details in the given subscription and provider.

## SYNTAX

### List (Default)
```
Get-AzProviderHubResourceTypeRegistration -ProviderNamespace <String> [-SubscriptionId <String[]>]
 [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### Get
```
Get-AzProviderHubResourceTypeRegistration -ProviderNamespace <String> [-SubscriptionId <String[]>]
 -ResourceType <String> [-DefaultProfile <PSObject>] [<CommonParameters>]
```

### GetViaIdentityProviderRegistration
```
Get-AzProviderHubResourceTypeRegistration -ResourceType <String>
 -ProviderRegistrationInputObject <IProviderHubIdentity> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

### GetViaIdentity
```
Get-AzProviderHubResourceTypeRegistration -InputObject <IProviderHubIdentity> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION
Gets a resource type details in the given subscription and provider.

## EXAMPLES

### Example 1: List all resource types under the resource provider namespace.
```powershell
Get-AzProviderHubResourceTypeRegistration -ProviderNamespace "Microsoft.Contoso"
```

```output
Name                        Type
----                        ----
testResourceType1           Microsoft.ProviderHub/providerRegistrations/resourceTypeRegistrations
testResourceType2           Microsoft.ProviderHub/providerRegistrations/resourceTypeRegistrations
```

List all resource types under the resource provider namespace.

### Example 2: Gets a resource type by name.
```powershell
Get-AzProviderHubResourceTypeRegistration -ProviderNamespace "Microsoft.Contoso" -ResourceType "testResourceType1"
```

```output
Name                        Type
----                        ----
testResourceType1           Microsoft.ProviderHub/providerRegistrations/resourceTypeRegistrations
```

Gets a resource type by name.

### Example 3: Gets a nested resource type by name.
```powershell
Get-AzProviderHubResourceTypeRegistration -ProviderNamespace "Microsoft.Contoso" -ResourceType "testResourceType1/nestedResourceType"
```

```output
Name                                      Type
----                                      ----
testResourceType1/nestedResourceType      Microsoft.ProviderHub/providerRegistrations/resourceTypeRegistrations
```

Gets a resource type by name.

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
Type: Microsoft.Azure.PowerShell.Cmdlets.ProviderHub.Models.IProviderHubIdentity
Parameter Sets: GetViaIdentity
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ProviderNamespace
The name of the resource provider hosted within ProviderHub.

```yaml
Type: System.String
Parameter Sets: List, Get
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderRegistrationInputObject
Identity Parameter

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.ProviderHub.Models.IProviderHubIdentity
Parameter Sets: GetViaIdentityProviderRegistration
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ResourceType
The resource type.

```yaml
Type: System.String
Parameter Sets: Get, GetViaIdentityProviderRegistration
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.

```yaml
Type: System.String[]
Parameter Sets: List, Get
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

### Microsoft.Azure.PowerShell.Cmdlets.ProviderHub.Models.IProviderHubIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.ProviderHub.Models.IResourceTypeRegistration

## NOTES

## RELATED LINKS
