### Chapter 9

* Powershell chains together multiple commands using a technique called pipeline parameter binding which in essence tries to feed the output of the first command as input to the second command.
* Pipeline parameter binding is achieved by either matching the cmdlet parameters `ByValue` or `ByPropertyName`. 
* Below is an example of `ByValue` parameter binding. Here the output of the first command is objects of type `System.Diagnostics.Process` and `Stop-Process` accepts this object type as `InputObject` parameter. Often cmdlets that have same nouns support `ByValue` parameter binding.

```powershell
Get-Process -Name note* | Stop-Process
```

* `ByPropertyName` parameter  binding matches one or more properties from the output objects of the first cmdlet to the parameter names of the second cmdlet. This is a simple name match as long as the matching parameter from the second cmdlet accepts pipeline input `ByPropertyName.`

* 


