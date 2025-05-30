---
external help file: Az.SpringCloud-help.xml
Module Name: Az.SpringCloud
online version: https://learn.microsoft.com/powershell/module/Az.SpringCloud/new-azspringcloudkeyvaultcertificateobject
schema: 2.0.0
content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/SpringCloud/SpringCloud/help/New-AzSpringCloudKeyVaultCertificateObject.md
original_content_git_url: https://github.com/Azure/azure-powershell/blob/main/src/SpringCloud/SpringCloud/help/New-AzSpringCloudKeyVaultCertificateObject.md
---

# New-AzSpringCloudKeyVaultCertificateObject

## SYNOPSIS
Create an in-memory object for KeyVaultCertificateProperties.

## SYNTAX

```
New-AzSpringCloudKeyVaultCertificateObject -Name <String> -VaultUri <String> [-Version <String>]
 [-ExcludePrivateKey <Boolean>] [<CommonParameters>]
```

## DESCRIPTION
Create an in-memory object for KeyVaultCertificateProperties.

## EXAMPLES

### Example 1: Create an in-memory object for KeyVaultCertificateProperties
```powershell
New-AzSpringCloudKeyVaultCertificateObject -VaultUri "keyvaluturi" -Name 'keycert'
```

```output
ActivateDate DnsName ExpirationDate IssuedDate Issuer SubjectName Thumbprint CertVersion ExcludePrivateKey KeyVaultCertName VaultUri
------------ ------- -------------- ---------- ------ ----------- ---------- ----------- ----------------- ---------------- --------
                                                                                                           keycert          keyvaluturi
```

Create an in-memory object for KeyVaultCertificateProperties

## PARAMETERS

### -ExcludePrivateKey
Optional.
If set to true, it will not import private key from key vault.

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The certificate name of key vault.

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

### -VaultUri
The vault uri of user key vault.

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

### -Version
The certificate version of key vault.

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

### Microsoft.Azure.PowerShell.Cmdlets.SpringCloud.Models.KeyVaultCertificateProperties

## NOTES

## RELATED LINKS
