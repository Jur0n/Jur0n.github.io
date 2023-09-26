---
layout: post
title: Windows PowerShell
tags: [SERV11F, PowerShell, ISE, ps1]
category: [PowerShell]
---

# Introducing Powershell

Windows  PowerShell is a commandline, which works object-oriented. It strongly looks like the command prompt one is already used to.
The command prompt does exsist since the first Operating System of Microsoft (MS-DOS). PowerShell is its worthy successor.
As already said, PowerShell works object-oriented, which means its commands do not only execute instructions, they can edit objects.

## Objects, CMdlets and Pipelines

PowerShell works with objects. A cmdlet creates an object, which is passed onto the next cmdlet. 
For example, a `Get` command creates an object and lists it to the screen. This output is formatted internaly and displayed to the user.
An object can be a procces, a service or an array of symbols. There are more than hunderd objects avaiable in PowerShell.


## First steps

`Get-Alias` give an overview to all MS-DOS commands and its PowerShell definitions.
Cmdlets follow the same pattern: a verb at first, like `Set` or `Get`, second a noun.

- `Set`: Data is changed or created 
- `Get`: Data is requested
- `Format`: Data is formated
- `Out`: created an output from data

with the use of the tabulator-button all possible option are shown.

Parameters always start with a `-`

- `Get-Help  %name%` shows help for a certain command
- `Update-Help` updates the "Help" directory   
- `Show-Command %name% ` provides a graphical interface for all parameters

- `get-command | group commandType` shows the quantity of all cmdlets , functions and aliases

The operator `|` is called a pipeline. Whith th euse of it, commands can be combined and forwarded to the next cmdlet

sort: with the use of `sort-object` the output can be sorted.
P.E.: `Get-Command | Sort-Object -Property Source` sorts the commands by its source. Parameters are `-descending` or `-ascending`.

### Date and Time

There are several options do display time with Powershell wit the use of ``get-Date`` :

``` Powershell
get-Date -format d
25.09.2023

get-Date -format t
10:25

get-Date -format T
10:25:36

get-Date -format HH:mm:ss:ff
10:25:49:11
```

#### The f-Operator

``` PS
"Es ist {0:dddd}, der {0:d},{0:t}" -f (Get-Date)
Es ist Montag, der 25.09.2023,10:27
```

With the use of the f-operator a String is read to the following command.

with the use of ``-`` two times can be subtracted.

``` PS 
PS C:\Users\Administrator> (get-date)-(get-date "1/1/2019 0:0:0")
Days              : 1728
Hours             : 10
Minutes           : 46
Seconds           : 36
Milliseconds      : 213
Ticks             : 1493379962135507
TotalDays         : 1728,44903024943
TotalHours        : 41482,7767259863
TotalMinutes      : 2488966,60355918
TotalSeconds      : 149337996,213551
TotalMilliseconds : 149337996213,551
```

It is possible to get the time from a different computer, but not with the use of ``Get-Date``. Therefore ``Win32_Currenttime`` has to be used.

``` PS
Get-CimInstance Win32_Currenttime -computername Win2019-2
```

### Drive-, Folder- and Datamanagement

#### Get-Drive

With the use of ``Get-Disk`` and ``Get-PsDrive`` you can get information about from the drives.

#### New-Item

`` New-Item`` creates new Data or Structure, with ``-type file or directory`` it can be further defined. `` ni`` is an alias for `` New-Item``.

#### Copy-Item

with ``Copy-Item`` data can be copied.

#### Move-Item

With ``Move-Item`` data can be moved.

#### Remove-Item

With ``Remove-Item`` data can be removed.

#### Get-Location / Test-Location

With ``Get-Location`` the current file-path is shown.

With ``Test-Location`` the given file-path is tested.

#### Measure-Object

`` dir | Measure-Object -property length sum`` 

With the use of the Commands the size and quantity can be read.
The number of all Files in a Subfolder can be found out with:

`` (Get-ChildItem -path $Env:Systemroot -Recourse).Count``

### Editing Textfiles

#### ``Get-Content``

Textfiles are read with ``Get-Content``

`` -path`` defines the path to the file. 

If only a certain line is to be read, arrays can be used:

``` PS
(Get-Content test.txt)[-2][0]
```
2-dimensional arrays are used. The First dimension defines the rows, the second the columns.
The can be counted positive or negative: 1 is the first, -1 the last column.

#### ``Set-Content``

A new file can be created with the use of ``Set-Content``.

``` PS
PS C:\Powershell> set-Content newtest.txt

Cmdlet Set-Content an der Befehlspipelineposition 1
Geben Sie Werte für die folgenden Parameter an:
Value[0]: This is a new File.
Value[1]:
PS C:\Powershell> Get-Content newtest.txt
This is a new File.
PS C:\Powershell>

```