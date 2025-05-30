---
external help file: Az.App-help.xml
Module Name: Az.App
online version: https://learn.microsoft.com/powershell/module/az.app/new-azcontainerappjob
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/App/App/help/New-AzContainerAppJob.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/App/App/help/New-AzContainerAppJob.md
---

# New-AzContainerAppJob

## SYNOPSIS
Create a Container Apps Job.

## SYNTAX

### CreateExpanded (Default)
```
New-AzContainerAppJob -Name <String> -ResourceGroupName <String> [-SubscriptionId <String>] -Location <String>
 [-ConfigurationRegistry <IRegistryCredentials[]>] [-ConfigurationReplicaRetryLimit <Int32>]
 [-ConfigurationReplicaTimeout <Int32>] [-ConfigurationSecret <ISecret[]>] [-ConfigurationTriggerType <String>]
 [-EnvironmentId <String>] [-EventTriggerConfigParallelism <Int32>]
 [-EventTriggerConfigReplicaCompletionCount <Int32>] [-EnableSystemAssignedIdentity]
 [-ManualTriggerConfigParallelism <Int32>] [-ManualTriggerConfigReplicaCompletionCount <Int32>]
 [-ScaleMaxExecution <Int32>] [-ScaleMinExecution <Int32>] [-ScalePollingInterval <Int32>]
 [-ScaleRule <IJobScaleRule[]>] [-ScheduleTriggerConfigCronExpression <String>]
 [-ScheduleTriggerConfigParallelism <Int32>] [-ScheduleTriggerConfigReplicaCompletionCount <Int32>]
 [-Tag <Hashtable>] [-TemplateContainer <IContainer[]>] [-TemplateInitContainer <IInitContainer[]>]
 [-TemplateVolume <IVolume[]>] [-UserAssignedIdentity <String[]>] [-WorkloadProfileName <String>]
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CreateViaJsonFilePath
```
New-AzContainerAppJob -Name <String> -ResourceGroupName <String> [-SubscriptionId <String>]
 -JsonFilePath <String> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CreateViaJsonString
```
New-AzContainerAppJob -Name <String> -ResourceGroupName <String> [-SubscriptionId <String>]
 -JsonString <String> [-DefaultProfile <PSObject>] [-AsJob] [-NoWait]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CreateViaIdentityExpanded
```
New-AzContainerAppJob -InputObject <IAppIdentity> -Location <String>
 [-ConfigurationRegistry <IRegistryCredentials[]>] [-ConfigurationReplicaRetryLimit <Int32>]
 [-ConfigurationReplicaTimeout <Int32>] [-ConfigurationSecret <ISecret[]>] [-ConfigurationTriggerType <String>]
 [-EnvironmentId <String>] [-EventTriggerConfigParallelism <Int32>]
 [-EventTriggerConfigReplicaCompletionCount <Int32>] [-EnableSystemAssignedIdentity]
 [-ManualTriggerConfigParallelism <Int32>] [-ManualTriggerConfigReplicaCompletionCount <Int32>]
 [-ScaleMaxExecution <Int32>] [-ScaleMinExecution <Int32>] [-ScalePollingInterval <Int32>]
 [-ScaleRule <IJobScaleRule[]>] [-ScheduleTriggerConfigCronExpression <String>]
 [-ScheduleTriggerConfigParallelism <Int32>] [-ScheduleTriggerConfigReplicaCompletionCount <Int32>]
 [-Tag <Hashtable>] [-TemplateContainer <IContainer[]>] [-TemplateInitContainer <IInitContainer[]>]
 [-TemplateVolume <IVolume[]>] [-UserAssignedIdentity <String[]>] [-WorkloadProfileName <String>]
 [-DefaultProfile <PSObject>] [-AsJob] [-NoWait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
Create a Container Apps Job.

## EXAMPLES

### Example 1: Create a Container Apps Job.
```powershell
$EnvId = (Get-AzContainerAppManagedEnv -ResourceGroupName azps_test_group_app -Name azps-env).Id
$probeHttpGetHttpHeader = New-AzContainerAppProbeHeaderObject -Name "Custom-Header" -Value "Awesome"
$probe = New-AzContainerAppProbeObject -Type "Liveness" -HttpGetPath "/health" -HttpGetPort 8080 -InitialDelaySecond 3 -PeriodSecond 3 -HttpGetHttpHeader $probeHttpGetHttpHeader
$temp = New-AzContainerAppTemplateObject -Image "mcr.microsoft.com/k8se/quickstart-jobs:latest" -Name "simple-hello-world-container" -Probe $probe -ResourceCpu 0.25 -ResourceMemory "0.5Gi"

New-AzContainerAppJob -Name azps-app-job -ResourceGroupName azps_test_group_app -Location eastus -ConfigurationReplicaRetryLimit 10 -ConfigurationReplicaTimeout 10 -ConfigurationTriggerType Manual -EnvironmentId $EnvId -ManualTriggerConfigParallelism 4 -ManualTriggerConfigReplicaCompletionCount 1 -TemplateContainer $temp
```

```output
Location Name         ProvisioningState ResourceGroupName
-------- ----         ----------------- -----------------
East US  azps-app-job Succeeded         azps_test_group_app
```

Create a Container Apps Job.

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

### -ConfigurationRegistry
Collection of private container registry credentials used by a Container apps job

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.IRegistryCredentials[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationReplicaRetryLimit
Maximum number of retries before failing the job.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationReplicaTimeout
Maximum number of seconds a replica is allowed to run.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationSecret
Collection of secrets used by a Container Apps Job

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.ISecret[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTriggerType
Trigger type of the job

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
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

### -EnableSystemAssignedIdentity
Determines whether to enable a system-assigned identity for the resource.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnvironmentId
Resource ID of environment.

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventTriggerConfigParallelism
Number of parallel replicas of a job that can run at a given time.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventTriggerConfigReplicaCompletionCount
Minimum number of successful replica completions before overall job completion.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
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
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.IAppIdentity
Parameter Sets: CreateViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JsonFilePath
Path of Json file supplied to the Create operation

```yaml
Type: System.String
Parameter Sets: CreateViaJsonFilePath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JsonString
Json string supplied to the Create operation

```yaml
Type: System.String
Parameter Sets: CreateViaJsonString
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Location
The geo-location where the resource lives

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ManualTriggerConfigParallelism
Number of parallel replicas of a job that can run at a given time.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ManualTriggerConfigReplicaCompletionCount
Minimum number of successful replica completions before overall job completion.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Job Name

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaJsonFilePath, CreateViaJsonString
Aliases: JobName

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

### -ResourceGroupName
The name of the resource group.
The name is case insensitive.

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaJsonFilePath, CreateViaJsonString
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScaleMaxExecution
Maximum number of job executions that are created for a trigger, default 100.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScaleMinExecution
Minimum number of job executions that are created for a trigger, default 0

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScalePollingInterval
Interval to check each event source in seconds.
Defaults to 30s

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScaleRule
Scaling rules.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.IJobScaleRule[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduleTriggerConfigCronExpression
Cron formatted repeating schedule ("* * * * *") of a Cron Job.

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduleTriggerConfigParallelism
Number of parallel replicas of a job that can run at a given time.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduleTriggerConfigReplicaCompletionCount
Minimum number of successful replica completions before overall job completion.

```yaml
Type: System.Int32
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SubscriptionId
The ID of the target subscription.

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaJsonFilePath, CreateViaJsonString
Aliases:

Required: False
Position: Named
Default value: (Get-AzContext).Subscription.Id
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tag
Resource tags.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateContainer
List of container definitions for the Container App.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.IContainer[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateInitContainer
List of specialized containers that run before app containers.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.IInitContainer[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateVolume
List of volume definitions for the Container App.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.App.Models.IVolume[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserAssignedIdentity
The array of user assigned identities associated with the resource.
The elements in array will be ARM resource ids in the form: '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ManagedIdentity/userAssignedIdentities/{identityName}.'

```yaml
Type: System.String[]
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkloadProfileName
Workload profile name to pin for container apps job execution.

```yaml
Type: System.String
Parameter Sets: CreateExpanded, CreateViaIdentityExpanded
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

### Microsoft.Azure.PowerShell.Cmdlets.App.Models.IAppIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.App.Models.IJob

## NOTES

## RELATED LINKS
