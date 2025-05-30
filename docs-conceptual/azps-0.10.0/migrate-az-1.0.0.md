---
title: All changes from AzureRM to Azure PowerShell Az 1.0.0
description: This migration guide contains a list of breaking changes made to Azure PowerShell in the Az version 1 release.
ms.devlang: powershell
ms.custom: devx-track-azurepowershell 
ms.service: azure-powershell
---
# Breaking changes for Az 1.0.0

This document provides detailed information on the changes between AzureRM 6.x and the new Az
module, version 1.x and later. The table of contents will help guide you through a full migration
path, including module-specific changes that may affect your scripts.

For general advice on getting started with a migration from AzureRM to Az, see [Start migration from
AzureRM to Az](migrate-from-azurerm-to-az.md).

> [!IMPORTANT]
> There have been breaking changes between Az 1.0.0 and Az 2.0.0 as well. After following this guide
> for updating from AzureRM to Az, see the [Az 2.0.0 breaking changes](migrate-az-2.0.0.md) to find out
> if you need to make additional changes.

## Table of Contents

- [General breaking changes](#general-breaking-changes)
  - [Cmdlet noun prefix changes](#cmdlet-noun-prefix-changes)
  - [Module name changes](#module-name-changes)
  - [Removed modules](#removed-modules)
  - [Windows PowerShell 5.1 and .NET 4.7.2](#windows-powershell-51-and-net-472)
  - [Temporary removal of user login using PSCredential](#temporary-removal-of-user-login-using-pscredential)
  - [Default device code login instead of web browser prompt](#default-device-code-login-instead-of-web-browser-prompt)
- [Module breaking changes](#module-breaking-changes)
  - [Az.ApiManagement (previously AzureRM.ApiManagement)](#azapimanagement-previously-azurermapimanagement)
  - [Az.Billing (previously AzureRM.Billing, AzureRM.Consumption, and AzureRM.UsageAggregates)](#azbilling-previously-azurermbilling-azurermconsumption-and-azurermusageaggregates)
  - [Az.CognitiveServices (previously AzureRM.CognitiveServices)](#azcognitiveservices-previously-azurermcognitiveservices)
  - [Az.Compute (previously AzureRM.Compute)](#azcompute-previously-azurermcompute)
  - [Az.DataFactory (previously AzureRM.DataFactories and AzureRM.DataFactoryV2)](#azdatafactory-previously-azurermdatafactories-and-azurermdatafactoryv2)
  - [Az.DataLakeAnalytics (previously AzureRM.DataLakeAnalytics)](#azdatalakeanalytics-previously-azurermdatalakeanalytics)
  - [Az.DataLakeStore (previously AzureRM.DataLakeStore)](#azdatalakestore-previously-azurermdatalakestore)
  - [Az.KeyVault (previously AzureRM.KeyVault)](#azkeyvault-previously-azurermkeyvault)
  - [Az.Media (previously AzureRM.Media)](#azmedia-previously-azurermmedia)
  - [Az.Monitor (previously AzureRM.Insights)](#azmonitor-previously-azurerminsights)
  - [Az.Network (previously AzureRM.Network)](#aznetwork-previously-azurermnetwork)
  - [Az.OperationalInsights (previously AzureRM.OperationalInsights)](#azoperationalinsights-previously-azurermoperationalinsights)
  - [Az.RecoveryServices (previously AzureRM.RecoveryServices, AzureRM.RecoveryServices.Backup, and AzureRM.RecoveryServices.SiteRecovery)](#azrecoveryservices-previously-azurermrecoveryservices-azurermrecoveryservicesbackup-and-azurermrecoveryservicessiterecovery)
  - [Az.Resources (previously AzureRM.Resources)](#azresources-previously-azurermresources)
  - [Az.ServiceFabric (previously AzureRM.ServiceFabric)](#azservicefabric-previously-azurermservicefabric)
  - [Az.Sql (previously AzureRM.Sql)](#azsql-previously-azurermsql)
  - [Az.Storage (previously Azure.Storage and AzureRM.Storage)](#azstorage-previously-azurestorage-and-azurermstorage)
  - [Az.Websites (previously AzureRM.Websites)](#azwebsites-previously-azurermwebsites)

## General breaking changes

This section details the general breaking changes that are part of the redesign of the Az module.

### Cmdlet Noun Prefix Changes

In the AzureRM module, cmdlets used either `AzureRM` or `Azure` as a noun prefix.  Az simplifies and normalizes cmdlet names, so that all cmdlets use 'Az' as their cmdlet noun prefix. For example:

```azurepowershell-interactive
Get-AzureRMVM
Get-AzureKeyVaultSecret
```

Has changed to:

```azurepowershell-interactive
Get-AzVM
Get-AzKeyVaultSecret
```

To make the transition to these new cmdlet names simpler, Az introduces two new cmdlets, [Enable-AzureRmAlias](/powershell/module/az.accounts/enable-azurermalias) and [Disable-AzureRmAlias](/powershell/module/az.accounts/disable-azurermalias).  `Enable-AzureRmAlias` creates aliases for the older cmdlet names in AzureRM that map to the newer Az cmdlet names. Using the `-Scope` argument with `Enable-AzureRmAlias` allows you to choose where aliases are enabled.

For example, the following script in AzureRM:

```azurepowershell-interactive
#Requires -Modules AzureRM.Storage
Get-AzureRmStorageAccount | Get-AzureStorageContainer | Get-AzureStorageBlob
```

Can be run with minimal changes using `Enable-AzureRmAlias`:

```azurepowershell-interactive
#Requires -Modules Az.Storage
Enable-AzureRmAlias -Scope Process
Get-AzureRmStorageAccount | Get-AzureStorageContainer | Get-AzureStorageBlob
```

Running `Enable-AzureRmAlias -Scope CurrentUser` will enable the aliases for all PowerShell sessions you open, so that after executing this cmdlet, a script like this would not need to be changed at all:

```azurepowershell-interactive
Get-AzureRmStorageAccount | Get-AzureStorageContainer | Get-AzureStorageBlob
```

For complete details on the usage of the alias cmdlets, see the [Enable-AzureRmAlias reference](/powershell/module/az.accounts/enable-azurermalias).

When you're ready to disable aliases, `Disable-AzureRmAlias` removes the created aliases. For complete details,
see the [Disable-AzureRmAlias reference](/powershell/module/az.accounts/disable-azurermalias).

> [!IMPORTANT]
> When disabling aliases, make sure that they are disabled for _all_ scopes which had aliases enabled.

### Module Name Changes

The module names have changed from `AzureRM.*` to `Az.*`, except for the following modules:

| AzureRM module | Az module |
|----------------|-----------|
| Azure.Storage | Az.Storage |
| Azure.AnalysisServices | Az.AnalysisServices |
| AzureRM.Profile | Az.Accounts |
| AzureRM.Insights | Az.Monitor |
| AzureRM.DataFactories | Az.DataFactory |
| AzureRM.DataFactoryV2 | Az.DataFactory |
| AzureRM.RecoveryServices.Backup | Az.RecoveryServices |
| AzureRM.RecoveryServices.SiteRecovery | Az.RecoveryServices |
| AzureRM.Tags | Az.Resources |
| AzureRM.MachineLearningCompute | Az.MachineLearning |
| AzureRM.UsageAggregates | Az.Billing |
| AzureRM.Consumption | Az.Billing |

The changes in module names mean that any script that uses `#Requires` or `Import-Module` to load specific modules will need to be changed to use the new module instead. For modules where the cmdlet suffix has not changed,
this means that although the module name has changed, the suffix indicating the operation space has _not_.

#### Migrating #Requires and Import-Module Statements

Scripts that use `#Requires` or `Import-Module` to declare a dependency on AzureRM modules must be updated to use the new module names. For example:

```azurepowershell-interactive
#Requires -Module AzureRM.Compute
```

Should be changed to:

```azurepowershell-interactive
#Requires -Module Az.Compute
```

For `Import-Module`:

```azurepowershell-interactive
Import-Module -Name AzureRM.Compute
```

Should be changed to:

```azurepowershell-interactive
Import-Module -Name Az.Compute
```

### Migrating Fully-Qualified Cmdlet Invocations

Scripts that use module-qualified cmdlet invocations, such as:

```azurepowershell-interactive
AzureRM.Compute\Get-AzureRmVM
```

Must be changed to use the new module and cmdlet names:

```azurepowershell-interactive
Az.Compute\Get-AzVM
```

### Migrating module manifest dependencies

Modules that express dependencies on AzureRM modules through a module manifest (.psd1) file will need to updated the module names in their `RequiredModules` section:

```powershell
RequiredModules = @(@{ModuleName="AzureRM.Profile"; ModuleVersion="5.8.2"})
```

Must be changed to:

```powershell
RequiredModules = @(@{ModuleName="Az.Profile"; ModuleVersion="1.0.0"})
```

### Removed modules

The following modules have been removed:

- `AzureRM.Backup`
- `AzureRM.Compute.ManagedService`
- `AzureRM.Scheduler`

The tools for these services are no longer actively supported.  Customers are encouraged to move to alternative services as soon as it is convenient.

### Windows PowerShell 5.1 and .NET 4.7.2

Using Az with PowerShell 5.1 for Windows requires the installation of .NET Framework 4.7.2. Using PowerShell
Core 6.x or later does not require .NET Framework.

### Temporary removal of User login using PSCredential

Due to changes in the authentication flow for .NET Standard, we are temporarily removing user login via PSCredential. This capability will be re-introduced in the 1/15/2019 release for PowerShell 5.1 for Windows. This is discussed in detail in [this GitHub issue.](https://github.com/Azure/azure-powershell/issues/7430)

### Default device code login instead of web browser prompt

Due to changes in the authentication flow for .NET Standard, we are using device login as the default login flow during interactive login. Web browser based login will be re-introduced for PowerShell 5.1 for Windows as the default in the 1/15/2019 release. At that time, users will be able to choose device login using a Switch parameter.

## Module breaking changes

This section details specific breaking changes for individual modules and cmdlets.

### Az.ApiManagement (previously AzureRM.ApiManagement)

- Removed the following cmdlets:
  - New-AzureRmApiManagementHostnameConfiguration
  - Set-AzureRmApiManagementHostnames
  - Update-AzureRmApiManagementDeployment
  - Import-AzureRmApiManagementHostnameCertificate
  - Use **Set-AzApiManagement** cmdlet to set these properties instead
- Removed the following properties:
  - Removed property `PortalHostnameConfiguration`, `ProxyHostnameConfiguration`, `ManagementHostnameConfiguration` and `ScmHostnameConfiguration` of type `PsApiManagementHostnameConfiguration` from `PsApiManagementContext`. Instead use `PortalCustomHostnameConfiguration`, `ProxyCustomHostnameConfiguration`, `ManagementCustomHostnameConfiguration` and `ScmCustomHostnameConfiguration` of type `PsApiManagementCustomHostNameConfiguration`.
  - Removed property `StaticIPs` from PsApiManagementContext. The property has been split into `PublicIPAddresses` and `PrivateIPAddresses`.
  - Removed required property `Location` from New-AzureApiManagementVirtualNetwork cmdlet.

### Az.Billing (previously AzureRM.Billing, AzureRM.Consumption, and AzureRM.UsageAggregates)

- The `InvoiceName` parameter was removed from the `Get-AzConsumptionUsageDetail` cmdlet.  Scripts will need to use other identity parameters for the invoice.

### Az.CognitiveServices (previously AzureRM.CognitiveServices)

- Removed `GetSkusWithAccountParamSetName` parameter set from `Get-AzCognitiveServicesAccountSkus` cmdlet.  You must get Skus by Account Type and Location, instead of using ResourceGroupName and Account Name.

### Az.Compute (previously AzureRM.Compute)

- `IdentityIds` are removed from `Identity` property in `PSVirtualMachine` and `PSVirtualMachineScaleSet` objects
  Scripts should no longer use the value of this field to make processing decisions.
- The type of `InstanceView` property of `PSVirtualMachineScaleSetVM` object is changed from `VirtualMachineInstanceView` to `VirtualMachineScaleSetVMInstanceView`
- `AutoOSUpgradePolicy` and `AutomaticOSUpgrade` properties are removed from `UpgradePolicy` property
- The type of `Sku` property in `PSSnapshotUpdate` object is changed from `DiskSku` to `SnapshotSku`
- `VmScaleSetVMParameterSet` is removed from `Add-AzVMDataDisk` cmdlet, you can no longer add a data disk individually to a ScaleSet VM.

### Az.DataFactory (previously AzureRM.DataFactories and AzureRM.DataFactoryV2)

- The `GatewayName` parameter has become mandatory in the `New-AzDataFactoryEncryptValue` cmdlet
- Removed `New-AzDataFactoryGatewayKey` cmdlet
- Removed `LinkedServiceName` parameter from `Get-AzDataFactoryV2ActivityRun` cmdlet
  Scripts should no longer use the value of this field to make processing decisions.

### Az.DataLakeAnalytics (previously AzureRM.DataLakeAnalytics)

- Removed deprecated cmdlets: `New-AzDataLakeAnalyticsCatalogSecret`, `Remove-AzDataLakeAnalyticsCatalogSecret`, and `Set-AzDataLakeAnalyticsCatalogSecret`

### Az.DataLakeStore (previously AzureRM.DataLakeStore)

- The following cmdlets have had the `Encoding` parameter changed from the type `FileSystemCmdletProviderEncoding` to `System.Text.Encoding`. This change removes the encoding values `String` and `Oem`. All the other prior encoding values remain.
  - New-AzureRmDataLakeStoreItem
  - Add-AzureRmDataLakeStoreItemContent
  - Get-AzureRmDataLakeStoreItemContent
- Removed deprecated `Tags` property alias from `New-AzDataLakeStoreAccount` and `Set-AzDataLakeStoreAccount` cmdlets

  Scripts using
  ```azurepowershell-interactive
  New-AzureRMDataLakeStoreAccount -Tags @{TagName="TagValue"}
  ```

  Should be changed to
  ```azurepowershell-interactive
  New-AzDataLakeStoreAccount -Tag @{TagName="TagValue"}
  ```

- Removed deprecated properties `Identity`, `EncryptionState`, `EncryptionProvisioningState`, `EncryptionConfig`, `FirewallState`, `FirewallRules`, `VirtualNetworkRules`, `TrustedIdProviderState`, `TrustedIdProviders`, `DefaultGroup`, `NewTier`, `CurrentTier`, `FirewallAllowAzureIps` from `PSDataLakeStoreAccountBasic` object.  Any script that
uses the `PSDatalakeStoreAccount` returned from `Get-AzDataLakeStoreAccount` should not reference these properties.

### Az.KeyVault (previously AzureRM.KeyVault)

- The `PurgeDisabled` property was removed from the `PSKeyVaultKeyAttributes`, `PSKeyVaultKeyIdentityItem`, and `PSKeyVaultSecretAttributes` objects
  Scripts should no longer reference the ```PurgeDisabled``` property to make processing decisions.

### Az.Media (previously AzureRM.Media)

- Remove deprecated `Tags` property alias from `New-AzMediaService` cmdlet
  Scripts using
  ```azurepowershell-interactive
  New-AzureRMMediaService -Tags @{TagName="TagValue"}
  ```

  Should be changed to
  ```azurepowershell-interactive
  New-AzMediaService -Tag @{TagName="TagValue"}
  ```

### Az.Monitor (previously AzureRM.Insights)

- Removed plural names `Categories` and `Timegrains` parameter in favor of singular parameter names from `Set-AzDiagnosticSetting` cmdlet
  Scripts using
  ```azurepowershell-interactive
  Set-AzureRmDiagnosticSetting -Timegrains PT1M -Categories Category1, Category2
  ```

  Should be changed to
  ```azurepowershell-interactive
  Set-AzDiagnosticSetting -Timegrain PT1M -Category Category1, Category2
  ```

### Az.Network (previously AzureRM.Network)

- Removed deprecated `ResourceId` parameter from `Get-AzServiceEndpointPolicyDefinition` cmdlet
- Removed deprecated `EnableVmProtection` property from `PSVirtualNetwork` object
- Removed deprecated `Set-AzVirtualNetworkGatewayVpnClientConfig` cmdlet

Scripts should no longer make processing decisions based on the values fo these fields.

### Az.OperationalInsights (previously AzureRM.OperationalInsights)

- Default parameter set for `Get-AzOperationalInsightsDataSource` is removed, and `ByWorkspaceNameByKind` has become the default parameter set

  Scripts that listed data sources using
  ```azurepowershell-interactive
  Get-AzureRmOperationalInsightsDataSource
  ```

  Should be changed to specify a Kind
  ```azurepowershell-interactive
  Get-AzOperationalInsightsDataSource -Kind AzureActivityLog
  ```

### Az.RecoveryServices (previously AzureRM.RecoveryServices, AzureRM.RecoveryServices.Backup, and AzureRM.RecoveryServices.SiteRecovery)

- Removed `Encryption` parameter from `New/Set-AzRecoveryServicesAsrPolicy` cmdlet
- `TargetStorageAccountName` parameter is now mandatory for managed disk restores in `Restore-AzRecoveryServicesBackupItem` cmdlet
- Removed `StorageAccountName` and `StorageAccountResourceGroupName` parameters in `Restore-AzRecoveryServicesBackupItem` cmdlet
- Removed `Name`parameter in `Get-AzRecoveryServicesBackupContainer` cmdlet

### Az.Resources (previously AzureRM.Resources)

- Removed `Sku` parameter from `New/Set-AzPolicyAssignment` cmdlet
- Removed `Password` parameter from `New-AzADServicePrincipal` and `New-AzADSpCredential` cmdlet
  Passwords are automatically generated, scripts that provided the password:

  ```azurepowershell-interactive
  New-AzAdSpCredential -ObjectId 00001111-aaaa-2222-bbbb-3333cccc4444 -Password $secPassword
  ```

  Should be changed to retrieve the password from the output:

  ```azurepowershell-interactive
  $credential = New-AzAdSpCredential -ObjectId 00001111-aaaa-2222-bbbb-3333cccc4444
  $secPassword = $credential.Secret
  ```

### Az.ServiceFabric (previously AzureRM.ServiceFabric)

- The following cmdlet return types have been changed:
  - The property `ServiceTypeHealthPolicies` of type `ApplicationHealthPolicy` has been removed.
  - The property `ApplicationHealthPolicies` of type `ClusterUpgradeDeltaHealthPolicy` has been removed.
  - The property `OverrideUserUpgradePolicy` of type `ClusterUpgradePolicy` has been removed.
  - These changes affect the following cmdlets:
    - Add-AzServiceFabricClientCertificate
    - Add-AzServiceFabricClusterCertificate
    - Add-AzServiceFabricNode
    - Add-AzServiceFabricNodeType
    - Get-AzServiceFabricCluster
    - Remove-AzServiceFabricClientCertificate
    - Remove-AzServiceFabricClusterCertificate
    - Remove-AzServiceFabricNode
    - Remove-AzServiceFabricNodeType
    - Remove-AzServiceFabricSetting
    - Set-AzServiceFabricSetting
    - Set-AzServiceFabricUpgradeType
    - Update-AzServiceFabricDurability
    - Update-AzServiceFabricReliability

### Az.Sql (previously AzureRM.Sql)

- Removed `State` and `ResourceId` parameters from `Set-AzSqlDatabaseBackupLongTermRetentionPolicy` cmdlet
- Removed deprecated cmdlets: `Get/Set-AzSqlServerBackupLongTermRetentionVault`, `Get/Start/Stop-AzSqlServerUpgrade`, `Get/Set-AzSqlDatabaseAuditingPolicy`, `Get/Set-AzSqlServerAuditingPolicy`, `Remove-AzSqlDatabaseAuditing`, `Remove-AzSqlServerAuditing`
- Removed deprecated parameter `Current` from `Get-AzSqlDatabaseBackupLongTermRetentionPolicy` cmdlet
- Removed deprecated parameter `DatabaseName` from `Get-AzSqlServerServiceObjective` cmdlet
- Removed deprecated parameter `PrivilegedLogin` from `Set-AzSqlDatabaseDataMaskingPolicy` cmdlet

### Az.Storage (previously Azure.Storage and AzureRM.Storage)

- To support creating an Oauth storage context with only the storage account name, the default parameter set has been changed to `OAuthParameterSet`
  - Example: `$ctx = New-AzureStorageContext -StorageAccountName $accountName`
- The `Location` parameter has become mandatory in the `Get-AzStorageUsage` cmdlet
- The Storage API methods now use the Task-based Asynchronous Pattern (TAP), instead of synchronous API calls. The following examples demonstrate the new asynchronous commands:

#### Blob Snapshot

AzureRM:

```azurepowershell-interactive
$b = Get-AzureStorageBlob -Container $containerName -Blob $blobName -Context $ctx
$b.ICloudBlob.Snapshot()
```

Az:

```azurepowershell-interactive
$b = Get-AzStorageBlob -Container $containerName -Blob $blobName -Context $ctx
$task = $b.ICloudBlob.SnapshotAsync()
$task.Wait()
$snapshot = $task.Result
```

#### Share Snapshot

AzureRM:

```azurepowershell-interactive
$Share = Get-AzureStorageShare -Name $containerName -Context $ctx
$snapshot = $Share.Snapshot()
```

Az:

```azurepowershell-interactive
$Share = Get-AzStorageShare -Name $containerName -Context $ctx
$task = $Share.SnapshotAsync()
$task.Wait()
$snapshot = $task.Result
```

#### Undelete soft-deleted blob

AzureRM:

```azurepowershell-interactive
$b = Get-AzureStorageBlob -Container $containerName -Blob $blobName -IncludeDeleted -Context $ctx
$b.ICloudBlob.Undelete()
```

Az:

```azurepowershell-interactive
$b = Get-AzStorageBlob -Container $containerName -Blob $blobName -IncludeDeleted -Context $ctx
$task = $b.ICloudBlob.UndeleteAsync()
$task.Wait()
```

#### Set Blob Tier

AzureRM:

```azurepowershell-interactive
$blockBlob = Get-AzureStorageBlob -Container $containerName -Blob $blockBlobName -Context $ctx
$blockBlob.ICloudBlob.SetStandardBlobTier("hot")

$pageBlob = Get-AzureStorageBlob -Container $containerName -Blob $pageBlobName -Context $ctx
$pageBlob.ICloudBlob.SetPremiumBlobTier("P4")
```

Az:

```azurepowershell-interactive
$blockBlob = Get-AzStorageBlob -Container $containerName -Blob $blockBlobName -Context $ctx
$task = $blockBlob.ICloudBlob.SetStandardBlobTierAsync("hot")
$task.Wait()

$pageBlob = Get-AzStorageBlob -Container $containerName -Blob $pageBlobName -Context $ctx
$task = $pageBlob.ICloudBlob.SetPremiumBlobTierAsync("P4")
$task.Wait()
```

### Az.Websites (previously AzureRM.Websites)

- Removed deprecated properties from the `PSAppServicePlan`, `PSCertificate`, `PSCloningInfo`, and `PSSite` objects
