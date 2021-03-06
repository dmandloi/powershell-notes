### Chapter 4

* cmdlets follow a _verb-noun_ naming convention. For your own cmdlets, noun can be anything. But verbs must be from the list of allowable verbs. To get a list of allowable verbs use, `Get-Verb` 
* To get a cmdlet name for an alias, use

```powershell
Get-Alias dir
```

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           dir -> Get-ChildItem
```

* To get the alias for a cmdlet, use

```powershell
Get-Alias -Definition Get-ChildItem
```

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

* `Show-Command` can be used to specify the parameters of a cmdlet using a GUI.
* In order to skip the parameter parsing by powershell when calling external commands use `--%` after the name of the external command. For example,

```powershell
python --% --version
```



