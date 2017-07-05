### Chapter 8

* To list the members \(i.e. properties and methods\) available on any powershell object, use `Get-Member` cmdlet.
* Objects can have different types of properties such a _Property, AliasProperty, ScriptProperty,_ and _NoteProperty_. Out of these only properties of type _Property_ are actually defined on the native powershell objects. Other types are dynamically created by the shell such as an _AliasProperty_ which is a P_roperty_  renamed to something else.
* Some of the useful cmdlets to work with the objects are `Select-Object`, `Sort-Object`, and `Where-Object`. `Select-Object` allows you to select certain properties from objects but `Where-Object` allows you to filter objects based on certain criteria. 

* 


