---
external help file: Az.Resources-help.xml
Module Name: Az.Resources
online version: https://learn.microsoft.com/powershell/module/az.resources/get-azroleeligibilityscheduleinstance
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Resources/Resources/help/Get-AzRoleEligibilityScheduleInstance.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/Resources/Resources/help/Get-AzRoleEligibilityScheduleInstance.md
---

# Get-AzRoleEligibilityScheduleInstance

## SYNOPSIS
Gets the specified role eligibility schedule instance.

## SYNTAX

### List (Default)
```
Get-AzRoleEligibilityScheduleInstance -Scope <String> [-Filter <String>] [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

### Get
```
Get-AzRoleEligibilityScheduleInstance -Name <String> -Scope <String> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

### GetViaIdentity
```
Get-AzRoleEligibilityScheduleInstance -InputObject <IAuthorizationIdentity> [-DefaultProfile <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION
Gets the specified role eligibility schedule instance.

## EXAMPLES

### Example 1: List all role eligible schedule instances for a resource
```powershell
$scope = "/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d"
Get-AzRoleEligibilityScheduleInstance -Scope $scope
```

```output
Name                                 Type                                            Scope
----                                 ----                                            -----
986d4ad8-f513-4a21-92e5-7163486e9e7c Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d
2066f412-e9bf-406a-962c-df8c16c9f9a0 Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/resourceGroups/UTSept3/providers/Microsoft.Compute/virtualMachines/vmtest123
f402cab4-83ab-4361-8725-2190bbe1ea6b Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/resourceGroups/sbo-test/providers/Microsoft.Web/connections/office365-1
5a12ea85-419e-426b-81f8-20e53808a14c Microsoft.Authorization/roleEligibilityScheduleInstances /providers/Microsoft.Management/managementGroups/PrimaryMG1
```

Returns all `roleEligibilityScheduleInstances` for the `scope`.
To call the API, you must have access to the `Microsoft.Authorization/roleAssignments/read` operation at the specified scope.

### Example 2: List all My role eligible schedule instances for a resource
```powershell
$scope = "/" # "/" stands for tenant level resource
Get-AzRoleEligibilityScheduleInstance -Scope $scope -Filter "asTarget()"
```

```output
Name                                 Type                                            Scope                                                 RoleDefinitionId
----                                 ----                                            -----                                                 ----------------                                                                      
4cd7e26b-8eca-425c-969d-ec708c88bf18 Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d   /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/providers/Microsoft.Authorizatio… 
00001111-aaaa-2222-bbbb-3333cccc4444 Microsoft.Authorization/roleEligibilityScheduleInstances /providers/Microsoft.Management/managementGroups/MG-3 /providers/Microsoft.Authorization/roleDefinitions/8e3af657-a8ff-443c-a75c-2fe8c4bcb… 
00001111-aaaa-2222-bbbb-3333cccc4444 Microsoft.Authorization/roleEligibilityScheduleInstances /providers/Microsoft.Management/managementGroups/MG-2 /providers/Microsoft.Authorization/roleDefinitions/8e3af657-a8ff-443c-a75c-2fe8c4bcb… 
00001111-aaaa-2222-bbbb-3333cccc4444 Microsoft.Authorization/roleEligibilityScheduleInstances /providers/Microsoft.Management/managementGroups/MG-1 /providers/Microsoft.Authorization/roleDefinitions/8e3af657-a8ff-443c-a75c-2fe8c4bcb…
```

Returns all `roleEligibilityScheduleInstances` for the `scope` which are assigned to the calling user.

### Example 3: List all role eligible schedule instances for a resource with filters
```powershell
$scope = "/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d"
$filter = "roleDefinitionId eq '/providers/Microsoft.Authorization/roleDefinitions/00001111-aaaa-2222-bbbb-3333cccc4444'"
Get-AzRoleEligibilityScheduleInstance -Scope $scope -Filter $filter
```

```output
Name                                 Type                                            Scope                                                                                 RoleDefinitionId
----                                 ----                                            -----                                                                                 ----------------                                      
314aa57e-064d-46c3-964e-a0d20989c1a2 Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d                                   /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/… 
496794ce-4465-4621-83aa-0b73b3c6fe17 Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d                                   /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/… 
6461530a-4d10-400e-9eb0-ff7cb73c4ffd Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d                                   /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/… 
d8daef6c-75da-42eb-9291-7cbc466d5b4b Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d                                   /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/…
```

Supported filters:
| Filter | Description |
| --- | --- |
| `atScope()` | List role assignments for only the specified scope, not including the role assignments at subscopes.
|
| `principalId eq '{objectId}'` | List role assignments for a specified user, group, or service principal.
|
| `roleDefinitionId eq '{roleDefinitionId}'` | List role assignments for a specified role definition.
|
| `status eq '{status}'` | List role assignments for a specified status.
|
| `assignedTo('{objectId}')` | List role assignments for a specified user, including ones inherited from groups.
|
| `asTarget()` | List role assignments for the current user or service principal, including ones inherited from groups.
|
| `assignedTo('{objectId}')+and+atScope()` | List role assignments for a specified user, including ones inherited from groups for only the specified scope, not including the role assignments at subscopes.|

### Example 4: Get a role eligible schedule instances by scope and name
```powershell
$scope = "/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d"
Get-AzRoleEligibilityScheduleInstance -Scope $scope -Name "4cd7e26b-8eca-425c-969d-ec708c88bf18"
```

```output
Name                                 Type                                            Scope                                               RoleDefinitionId
----                                 ----                                            -----                                               ----------------                                                                        
4cd7e26b-8eca-425c-969d-ec708c88bf18 Microsoft.Authorization/roleEligibilityScheduleInstances /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d /subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/providers/Microsoft.Authorization/…
```

Use the `Id` property to get `scope` and `name`

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

### -Filter
The filter to apply on the operation.
Use $filter=atScope() to return all role assignment schedules at or above the scope.
Use $filter=principalId eq {id} to return all role assignment schedules at, above or below the scope for the specified principal.
Use $filter=assignedTo('{userId}') to return all role eligibility schedules for the user.
Use $filter=asTarget() to return all role eligibility schedules created for the current user.

```yaml
Type: System.String
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Identity Parameter
To construct, see NOTES section for INPUTOBJECT properties and create a hash table.

```yaml
Type: Microsoft.Azure.PowerShell.Cmdlets.Resources.Authorization.Models.IAuthorizationIdentity
Parameter Sets: GetViaIdentity
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
The name (hash of schedule name + time) of the role eligibility schedule to get.

```yaml
Type: System.String
Parameter Sets: Get
Aliases: RoleEligibilityScheduleInstanceName

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope
The scope of the role eligibility schedules.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Resources.Authorization.Models.IAuthorizationIdentity

## OUTPUTS

### Microsoft.Azure.PowerShell.Cmdlets.Resources.Authorization.Models.Api20201001Preview.IRoleEligibilityScheduleInstance

## NOTES

## RELATED LINKS
