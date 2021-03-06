### Chapter 9

* Powershell chains together multiple commands using a technique called pipeline parameter binding which in essence tries to feed the output of the first command as input to the second command.
* Pipeline parameter binding is achieved by either matching the cmdlet parameters `ByValue` or `ByPropertyName`. 
* Below is an example of `ByValue` parameter binding. Here the output of the first command is objects of type `System.Diagnostics.Process` and `Stop-Process` accepts this object type as `InputObject` parameter. Often cmdlets that have same nouns support `ByValue` parameter binding.

```powershell
Get-Process -Name note* | Stop-Process
```

* `ByPropertyName` parameter  binding matches one or more properties from the output objects of the first cmdlet to the parameter names of the second cmdlet. This is a simple name match as long as the matching parameter from the second cmdlet accepts pipeline input `ByPropertyName.`

* Pipeline can be used to apply a field mapping to the contents of a CSV file. Below example assumes a CSV with the following content and then maps the column names `login` and `dept` as `name` and `department` so that they can be matched to other cmdlet parameters down the pipeline.

```csv
login,dept,city,title
DonJ,IT,Las Vegas,CTO
GregS,Custodial,Denver,Janitor
JeffH,IT,Syracuse,Network Engineer
```

```powershell
Import-CSV users.csv | Select-Object -Property city,title
@{name="name"; expression={$_.login}},
@{name="department"; expression={$_.dept}}
```

```
city      title            name  department
----      -----            ----  ----------
Las Vegas CTO              DonJ  IT
Denver    Janitor          GregS Custodial
Syracuse  Network Engineer JeffH IT
```

* `ExpandProperty` parameter of `Select-Object` cmdlet can be used to get a list of strings from the property values of the objects. The below example illustrates the difference between `Property` and `ExpandProperty` parameters of the `Select-Object` cmdlet. Note how the type of object returned by `Select-Object` is different.

```powershell
Get-Process -Name chrome | Select-Object -Property Name | Get-Member
```

```
 TypeName: Selected.System.Diagnostics.Process
```

```powershell
Get-Process -Name chrome | Select-Object -ExpandProperty Name | Get-Member
```

```
TypeName: System.String
```

* cmdlets placed inside the parenthesis are executed first. This technique can be used to achieve pipeline parameter binding `ByPropertyName` in some cases. The below example specifies the `ComputerName` parameter by reading the content of a text file containing computer names.

```powershell
Get-Process -ComputerName (Get-Content .\computers.txt) 
```



