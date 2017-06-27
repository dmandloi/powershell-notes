### Chapter 5

* A PowerShell provider is designed to take some kind of _data storage_ and make it look like a \_disk drive. \_To list all the available PSProviders use `Get-PSProvider.`

* A PowerShell drive uses a single provider to connect to a data storage. To list all the available PSDrives use `Get-PSDrive.`

* Each PSProvider models a data store using hierachical objects similar to drives, folders and files found in the windows file system.

* The below example shows how to temporarily \(i.e. only within the current PowerShell session\) map a file share at `\\Server\share`  to drive `Z.`

```powershell
New-PSDrive -PSProvider FileSystem -Name Z -Root \\Server\share
```

* The below example shows the value of environment variable `TEMP.`

```powershell
dir env:TEMP
```

* The below example shows how to update the value of the registry key `HideFileExt.`

```powershell
Set-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced -Name HideFileExt -Value 0
```

* By default the Registry PSProvider only allows access to `HKCU` and `HKLM` drives. To access other registry hives, such as HKEY\_USERS that stores registry keys for other windows users, you need to first create a new PSDrive and then any keys and values can be accessed using the item cmdlets. The below example shows how to view the temp directory location of another user. 

```powershell
New-PSDrive -PSProvider Registry -NAME HKU -Root HKEY_USERS
Get-ItemProperty HKU:\S-1-5-21-1848062460-3353792045-4041816196-1001\Environment | Select TEMP
```



