These are my notes from reading Learn Windows PowerShell in a month of lunches 3rd Edition.

### Chapter 3

* `Help` combines `Get-Help` and `More`cmdlet.
* cmdlets, functions, and workflows are collectively known as commands.
* `Get-Command` lets you find commands matching a string. For example, below lists all commands that include the string **smbshare**

```powershell
Get-Command *smbshare*
```

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Block-SmbShareAccess                               2.0.0.0    SmbShare
Function        Get-SmbShare                                       2.0.0.0    SmbShare
Function        Get-SmbShareAccess                                 2.0.0.0    SmbShare
Function        Grant-SmbShareAccess                               2.0.0.0    SmbShare
Function        New-SmbShare                                       2.0.0.0    SmbShare
Function        Remove-SmbShare                                    2.0.0.0    SmbShare
Function        Revoke-SmbShareAccess                              2.0.0.0    SmbShare
Function        Set-SmbShare                                       2.0.0.0    SmbShare
Function        Unblock-SmbShareAccess                             2.0.0.0    SmbShare
```

* 




