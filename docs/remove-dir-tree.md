Script: *remove-dir-tree.ps1*
========================

This PowerShell script silently removes a directory tree recursively. Use it with care!

Parameters
----------
```powershell
PS> ./remove-dir-tree.ps1 [[-pathToDirTree] <String>] [<CommonParameters>]

-pathToDirTree <String>
    Specifies the file path to the directory tree
    
    Required?                    false
    Position?                    1
    Default value                
    Accept pipeline input?       false
    Accept wildcard characters?  false

[<CommonParameters>]
    This script supports the common parameters: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, 
    WarningVariable, OutBuffer, PipelineVariable, and OutVariable.
```

Example
-------
```powershell
PS> ./remove-dir-tree.ps1 C:\Temp

```

Notes
-----
Author: Markus Fleschutz | License: CC0

Related Links
-------------
https://github.com/fleschutz/PowerShell

Script Content
--------------
```powershell
<#
.SYNOPSIS
        Removes a dir tree
.DESCRIPTION
        This PowerShell script silently removes a directory tree recursively. Use it with care!
.PARAMETER pathToDirTree
        Specifies the file path to the directory tree
.EXAMPLE
        PS> ./remove-dir-tree.ps1 C:\Temp
.LINK
        https://github.com/fleschutz/PowerShell
.NOTES
        Author: Markus Fleschutz | License: CC0
#>

param([string]$pathToDirTree = "")

try {
	if ($pathToDirTree -eq "" ) { $pathToDirTree = Read-Host "Enter the path to the directory tree" }

	Remove-Item -Force -Recurse -Confirm:$false $pathToDirTree

	exit 0 # success
} catch {
        "⚠️ Error in line $($_.InvocationInfo.ScriptLineNumber): $($Error[0])"
        exit 1
}
```

*(generated by convert-ps2md.ps1 using the comment-based help of remove-dir-tree.ps1 as of 03/27/2024 17:36:31)*