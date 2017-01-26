---
author: brianlic-msft
description: 
external help file: HgsServer-help.xml
keywords: powershell, cmdlet
manager: alanth
ms.date: 2016-12-20
ms.prod: powershell
ms.technology: powershell
ms.topic: reference
online version: 
schema: 2.0.0
title: Import-HgsServerState
ms.assetid: 73AD3A36-0BED-4BD0-A315-A6178C596A00
---

# Import-HgsServerState

## SYNOPSIS
Imports an exported Host Guardian Service state into a Host Guardian Service instance.

## SYNTAX

### XML
```
Import-HgsServerState [[-XML] <XmlDocument>] -Password <SecureString> [-ImportTpmModeState]
 [-ImportActiveDirectoryModeState] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### File
```
Import-HgsServerState [[-Path] <String>] -Password <SecureString> [-ImportTpmModeState]
 [-ImportActiveDirectoryModeState] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Import-HgsServer** cmdlet imports the previously exported Host Guardian Service (HGS) state to the existing Host Guardian Service instance.

The cmdlet imports the following Host Guardian Service state from the input file: 

- Attestation service policies
- Attestation service configuration data
- Key protection policies
- Key protection configuration data
- Key Protection Signer Certificates and private keys
- Key Protection Encryption Certificates and private keys

Additionally, this cmdlet renews the attestation service signer certificate and updates the key protection service instance with this certificate.

For more information about the scenario terms, see Security and Assurancehttp://go.microsoft.com/fwlink/?LinkId=699209 (http://go.microsoft.com/fwlink/?LinkId=699209).

## EXAMPLES

### Example 1: Import HGS state data
```
PS C:\>Import-HgsServerState -Path "C:\ExportedHgsServerState.xml" -Password $Pass
```

This command imports previously exported state on the current HGS server.
This command can be called on only one node.
The state is automatically replicated to other nodes in the HGS server setup.

The exported state is the output generated from **Export-HgsServerState** when run against an existing HGS server setup.
The password specified must match the password that was passed to Export-HgsServerState.

Use ConvertTo-SecureString to generate a secure string that represents the password.

## PARAMETERS

### -XML
Specifies the state that this cmdlet imports as an XML document.

```yaml
Type: XmlDocument
Parameter Sets: XML
Aliases: InputObject

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path of the file that this cmdlet imports.

```yaml
Type: String
Parameter Sets: File
Aliases: FilePath

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Password
Specifies the password that the Export-HgsServerState cmdlet used to encrypt the keys.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ImportTpmModeState
Indicates that this cmdlet imports and updates Attestation service configuration state relevant to the trusted platform module (TPM) operational mode.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ImportActiveDirectoryModeState
Indicates that this cmdlet imports and updates Attestation service configuration state relevant to the Active Directory operational mode.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

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
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Export-HgsServerState](./Export-HgsServerState.md)

[HGS Server Cmdlets](./index.md)
