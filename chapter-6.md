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

* 


