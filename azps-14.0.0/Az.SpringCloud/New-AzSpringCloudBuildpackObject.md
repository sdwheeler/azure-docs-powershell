---
external help file: Az.SpringCloud-help.xml
Module Name: Az.SpringCloud
online version: https://learn.microsoft.com/powershell/module/Az.SpringCloud/new-azspringcloudbuildpackobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/SpringCloud/SpringCloud/help/New-AzSpringCloudBuildpackObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/SpringCloud/SpringCloud/help/New-AzSpringCloudBuildpackObject.md
---

# New-AzSpringCloudBuildpackObject

## SYNOPSIS
Create an in-memory object for BuildpackProperties.

## SYNTAX

```
New-AzSpringCloudBuildpackObject [-Id <String>] [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for BuildpackProperties.

## EXAMPLES

### Example 1: Create an in-memory object for BuildpackProperties
```powershell
New-AzSpringCloudBuildpackObject -Id "tanzu-buildpacks/dotnet-core"
```

```output
Id
--
tanzu-buildpacks/dotnet-core
```

Create an in-memory object for BuildpackProperties

## PARAMETERS

### -Id
Id of the buildpack.

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

### Microsoft.Azure.PowerShell.Cmdlets.SpringCloud.Models.BuildpackProperties

## NOTES

## RELATED LINKS
