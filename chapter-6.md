### Chapter 6

* Output from cmdlets can be serealized to csv or xml files using `Export-Csv` and `Export-Clixml` cmdlets and deserialized  using `Import-Csv` and `Import-Clixml` cmdlets. The below example shows how to export a list of running process to a CSV file and import the information back in the console.

```powershell
Get-Process | Export-Csv c:\temp\procs.csv
Import-Csv c:\temp\procs.csv
```

* Two sets of objects can be compared using the `Compare-Object` \(alias `Diff`\) cmdlet. The below example finds the difference between the processes saved to an xml file and the current set of processes by only comparing their names.

```powershell
Diff -ReferenceObject (Import-Clixml c:\temp\procs.xml) -DifferenceObject (Get-Process) -Property Name
```

* The following two commands are syntactically the same. However using the `Out-File` approach provides more flexibility since all parameters supported by `Out-File` can be used.

```powershell
Dir > c:\temp\DirectoryList.txt
Dir | Out-File c:\temp\DirectoryList.txt
```

* `Out-GridView` sends the output to a UI with a table control and can be useful to see outputs of certain cmdlets such as `Get-Process`

```powershell
Get-Process | Out-GridView
```

* The ConvertTo-\* cmdlets, such as `ConvertTo-Json` , in powershell only convert the output of a cmdlet to a particular format. They do not write the output to a file. `Out-File` can then be used to write the converted format to a file. The below example shows how to get the list of process to a JSON file.

```powershell
Get-Process | ConvertTo-Json | Out-File C:\temp\procs.json
```

* The reverse of ConvertTo-\* cmdlets are ConvertFrom-\* cmdlets. The below example reads a JSON file containing process information as converts them to powershell objects.

```powershell
Get-Content -Raw c:\temp\procs.json | ConvertFrom-Json
```

* The `Import-Csv` and `Import-Clixml` cmdlets do the double duty of converting the output to a particular format and writing it to a file. On the other hand, `ConvertTo-Csv` and `ConvertTo-Xml`  cmdlets only convert the output to a particular format but do not write the output to a file.

* You can see what operations a command will perform without actually performing them by using the `-WhatIf` switch parameter.



