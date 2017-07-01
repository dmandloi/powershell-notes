### Chapter 6

* Output from cmdlets can be serealized to csv or xml files using `Export-Csv` and `Export-Clixml` cmdlets and deserialized  using `Import-Csv` and `Import-Clixml` cmdlets. The below example shows how to export a list of running process to a CSV file and import the information back in the console.

```powershell
Get-Process | Export-Csv c:\temp\procs.csv
Import-Csv c:\temp\procs.csv
```

* 


