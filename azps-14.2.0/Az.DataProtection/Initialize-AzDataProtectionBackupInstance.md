---
external help file: Az.DataProtection-help.xml
Module Name: Az.DataProtection
online version: https://learn.microsoft.com/powershell/module/az.dataprotection/initialize-azdataprotectionbackupinstance
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DataProtection/DataProtection/help/Initialize-AzDataProtectionBackupInstance.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/DataProtection/DataProtection/help/Initialize-AzDataProtectionBackupInstance.md
---

# Initialize-AzDataProtectionBackupInstance

## SYNOPSIS
Initializes Backup instance Request object for configuring backup

## SYNTAX

```
Initialize-AzDataProtectionBackupInstance -DatasourceType <DatasourceTypes> -DatasourceLocation <String>
 [-PolicyId <String>] [-DatasourceId <String>] [-SecretStoreURI <String>] [-SecretStoreType <SecretStoreTypes>]
 [-SnapshotResourceGroupId <String>] [-FriendlyName <String>]
 [-BackupConfiguration <IBackupDatasourceParameters>] [-UseSystemAssignedIdentity <Boolean>]
 [-UserAssignedIdentityArmId <String>] [<CommonParameters>]
```

## DESCRIPTION
Initializes Backup instance Request object for configuring backup

## EXAMPLES

### Example 1: Initialize Backup instance object for Azure Disk
```powershell
$policy = Get-AzDataProtectionBackupPolicy -SubscriptionId "xxxx-xxx-xxx" -ResourceGroupName sarath-rg -VaultName sarath-vault
$AzureDiskId = "/subscriptions/{subscription}/resourceGroups/{resourceGroup}/providers/Microsoft.Compute/disks/{diskname}"
$instance = Initialize-AzDataProtectionBackupInstance -DatasourceType AzureDisk -DatasourceLocation westus -DatasourceId $AzureDiskId -PolicyId $policy[0].Id
$instance.Property.PolicyInfo.PolicyParameter.DataStoreParametersList[0].ResourceGroupId = "/subscriptions/{subscription}/resourceGroups/{snapshotResourceGroup}"
$instance
```

```output
Name Type BackupInstanceName
---- ---- ------------------
          sarath-disk3-sarath-disk3-af697a80-e2bc-49f1-af6c-22f6c4d68405
```

The First command gets all the policies in a given vault.
The second command stores azure disk's resource id in $AzureDiskId
variable.
The third command returns a backup instance resource for Azure Disk.
The fourth command sets the snapshot resource group field.
This object can now be used to configure backup for the given disk.

### Example 2: Initialize Backup instance object for AzureKubernetesService
```powershell
$policy = Get-AzDataProtectionBackupPolicy -SubscriptionId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -VaultName "vaultName" -ResourceGroupName "resourceGroupName" | Where-Object {$_.Name -eq "policyName"}
$sourceClusterId = "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/resourceGroupName/providers/Microsoft.ContainerService/managedClusters/aks-cluster"
$snapshotResourceGroupId = "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/resourceGroupName"
$backupConfig = New-AzDataProtectionBackupConfigurationClientObject -SnapshotVolume $true -IncludeClusterScopeResource $true -DatasourceType AzureKubernetesService -LabelSelector "x=y","foo=bar" 
$backupInstance = Initialize-AzDataProtectionBackupInstance -DatasourceType AzureKubernetesService  -DatasourceLocation "eastus" -PolicyId $policy.Id -DatasourceId $sourceClusterId -SnapshotResourceGroupId $snapshotResourceGroupId -FriendlyName "aks-cluster-friendlyName" -BackupConfiguration $backupConfig
$instance
```

```output
Name BackupInstanceName
---- ------------------
     aks-cluster-aks-cluster-ed68435e-069t-4b4a-9d84-d0c194800fc2
```

The First command gets the AzureKubernetesService policy in a given vault.
The second, third command initializes the AKS cluster and snapshot resource group Id.
The fourth command backup configuration object needed for AzureKubernetesService.
The fifth command initializes the client object for backup instance.
This object can now be used to configure backup using New-AzDataProtectionBackupInstance after all necessary permissions are assigned with Set-AzDataProtectionMSIPermission command.

### Example 3: Configure protection for AzureDatabaseForPGFlexServer
```powershell
$vault = Get-AzDataProtectionBackupVault -SubscriptionId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -ResourceGroupName "resourceGroupName" -VaultName "vaultName"
$pol = Get-AzDataProtectionBackupPolicy -SubscriptionId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -VaultName "vaultName" -ResourceGroupName "resourceGroupName" -Name "policyName"
$datasourceId = "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/rgName/providers/Microsoft.DBforPostgreSQL/flexibleServers/test-pgflex"
$backupInstanceClientObject = Initialize-AzDataProtectionBackupInstance -DatasourceType AzureDatabaseForPGFlexServer -DatasourceLocation $vault.Location -PolicyId $pol[0].Id -DatasourceId $datasourceId
```

```output
Name BackupInstanceName
---- ------------------
     test-pgflex-test-pgflex-ed68435e-069t-4b4a-9d84-d0c194800fc2
```

The first command gets the backup vault.
The second command get the AzureDatabaseForPGFlexServer policy.
The third command datasource ARM Id.
The fourth command initializes the backup instance.
Similarly use datasourcetype AzureDatabaseForMySQL to initialize backup instance for AzureDatabaseForMySQL.

### Example 4: Initialize Backup instance object for Azure Blob Storage
```powershell
$storageAccountId = "/subscriptions/{subscriptionId}/resourcegroups/{resourceGroupName}/providers/Microsoft.Storage/storageAccounts/{storageAccountName}"
$vault = Get-AzDataProtectionBackupVault -ResourceGroupName $resourceGroupName -VaultName $vaultName 
$blobPolicy = Get-AzDataProtectionBackupPolicy -ResourceGroupName $resourceGroupName -VaultName $vault.Name -Name $policyName
$backupConfig = New-AzDataProtectionBackupConfigurationClientObject -DatasourceType AzureBlob -IncludeAllContainer -StorageAccountResourceGroupName $resourceGroupName -StorageAccountName $storageAccountName
$backupInstance = Initialize-AzDataProtectionBackupInstance -DatasourceType AzureBlob -DatasourceLocation $vault.Location -PolicyId $blobPolicy.Id -DatasourceId $storageAccountId -BackupConfiguration $backupConfig
$backupInstance
```

```output
Name BackupInstanceName
---- ------------------
     blobbackuptest-blobbackuptest-ed68435e-069t-4b4a-9d84-d0c194800fc2
```

The first command specifies the Blob storage account id.
The second command gets the backup vault.
The third command gets a Blob policy within the vault.
The fourth command initializes the backup configuration.
The fifth command initializes the backup instance.ype AzureDatabaseForMySQL to initialize backup instance for AzureDatabaseForMySQL.

## PARAMETERS

### -BackupConfiguration
Backup configuration for backup.
Use this parameter to configure protection for AzureKubernetesService,AzureBlob.
To construct, see NOTES section for BACKUPCONFIGURATION properties and create a hash table.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.DataProtection.Models.Api202501.IBackupDatasourceParameters
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DatasourceId
ID of the datasource to be protected

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

### -DatasourceLocation
Location of the Datasource to be protected.

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

### -DatasourceType
Datasource Type

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.DataProtection.Support.DatasourceTypes
Parameter Sets: (All)
Aliases:
Accepted values: AzureDisk, AzureBlob, AzureDatabaseForPostgreSQL, AzureKubernetesService, AzureDatabaseForPGFlexServer, AzureDatabaseForMySQL

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FriendlyName
Friendly name for backup instance

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

### -PolicyId
Policy Id to be associated to Datasource

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

### -SecretStoreType
Secret store type for secret store authentication of data source.
This parameter is only supported for AzureDatabaseForPostgreSQL currently.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.DataProtection.Support.SecretStoreTypes
Parameter Sets: (All)
Aliases:
Accepted values: AzureKeyVault

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecretStoreURI
Secret uri for secret store authentication of data source.
This parameter is only supported for AzureDatabaseForPostgreSQL currently.

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

### -SnapshotResourceGroupId
Snapshot Resource Group

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

### -UserAssignedIdentityArmId
User assigned identity ARM Id

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: AssignUserIdentity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSystemAssignedIdentity
Use system assigned identity

```yaml
Type: System.Nullable`1[System.Boolean]
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

### Microsoft.Azure.PowerShell.Cmdlets.DataProtection.Models.Api202501.IBackupInstanceResource

## NOTES

## RELATED LINKS
