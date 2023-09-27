---
layout: post
title: Introducing Windows PowerShell
tags: [SERV11F, PowerShell, ISE, powershell]
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

## Date and Time

There are several options do display time with Powershell wit the use of ``get-Date`` :

```powershell
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

```powershell
"Es ist {0:dddd}, der {0:d},{0:t}" -f (Get-Date)
Es ist Montag, der 25.09.2023,10:27
```

With the use of the f-operator a String is read to the following command.

with the use of ``-`` two times can be subtracted.

```powershell
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

```powershell
Get-CimInstance Win32_Currenttime -computername Win2019-2
```

## Drive-, Folder- and Datamanagement

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

```powershell
(Get-Content test.txt)[-2][0]
```
2-dimensional arrays are used. The First dimension defines the rows, the second the columns.
The can be counted positive or negative: 1 is the first, -1 the last column.

#### ``Set-Content``

A new file can be created with the use of ``Set-Content``.

```powershell
PS C:\Powershell> set-Content newtest.txt

Cmdlet Set-Content an der Befehlspipelineposition 1
Geben Sie Werte für die folgenden Parameter an:
Value[0]: This is a new File.
Value[1]:
PS C:\Powershell> Get-Content newtest.txt
This is a new File.
```

#### ``Add-Content``

With ``Add-Content`` new data can be added to a file.

```powershell
# This adds new text
add-content newtest.txt -value "NewText"

# A file can be added to another
add-content newtest.txt -value (get-content test.txt)
```

#### ``Clear-Content``

Clears a File.

#### Searching Files

```powershell
#a file can be searched with this command:
Get-ChildItem -Path test.txt | Select-String "dazu"

#Output:

PS C:\Powershell> Get-ChildItem -Path test.txt | Select-String "dazu"

test.txt:2:Und hier die zweite Zeile dazu.

```
#### Replacing Content

```powershell
# replace , with ;
(Get-Content test.txt) -replace " ",";"

#Output:
PS C:\powershell> (Get-Content test.txt) -replace " ",";"
Dies;ist;eien;Testdate.
Und;hier;die;zweite;Zeile;dazu.
Danach;die;dritte.
Gefolgt;von;der;vierten.
Die;Fünfte;ist;die;Letzte.Nummer;6.
PS C:\powershell>
```

The Output happens only in the Terminal screen. It is nothing changed in the file.

#### ``Get-Item``

Every Data and Folder has several attributes as name, length..

```powershell
PS C:\powershell> get-item test.txt


    Verzeichnis: C:\powershell


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       26.09.2023     16:28            141 test.txt


PS C:\powershell>
```
Some Values are read with ``Get-ItemProperty test.txt -name length``

```powershell
PS C:\powershell> Get-ItemProperty test.txt -name length


length       : 141
PSPath       : Microsoft.PowerShell.Core\FileSystem::C:\powershell\test.txt
PSParentPath : Microsoft.PowerShell.Core\FileSystem::C:\powershell
PSChildName  : test.txt
PSDrive      : C
PSProvider   : Microsoft.PowerShell.Core\FileSystem
```
### Attributes

| Parameter|definition |
|---|---|
|d-----|Directory|
|-a----|Archive (p.e. File)|
|--r---|ReadOnly|
|---h--|Hidden|
|----s-|Systemfile|
|-----l|Link|

All letters have a destined place. Combinations are possible.

#### ``Get-ItemProperty``

```powershell
PS C:\powershell> Get-ItemProperty test.txt -name mode


mode         : -ar---
PSPath       : Microsoft.PowerShell.Core\FileSystem::C:\powershell\test.txt
PSParentPath : Microsoft.PowerShell.Core\FileSystem::C:\powershell
PSChildName  : test.txt
PSDrive      : C
PSProvider   : Microsoft.PowerShell.Core\FileSystem
```

The File show the attributes _ar_. It´s a File which is in ReadOnly.

#### ``Set-ItemProperty``

Attributes can be changed with the use of ``Set-ItemProperty``

```powershell
Set-ItemProperty test.txt -name attributes -value ([System.IO.FileAttributes]::Hidden -bxor [System.IO.FileAttributes]::Archive)
```
Changes the Attributs to _hidden_ and _archive_.

In this example, the attributs are set as absolute, which means that already existing attributes are overwritten.

#### Making a lot of files

```powershell
1..500 | ForEach-Object {New-Item -ItemType File -Path ("Datei{0:000}.txt" -f $_)} 
```

This command creates 500 empty textfiles with a schema.

## Editing CSV- and logfiles

In Windows operating systems protocols are saved as logfiles. Those files are stored as text or as CSV-Files.
Those are system independet and include readable data seperated by commas. Every CSV file starts with headings.
A typical example is the **dcpromo.csv**. I contains information about the creation of a domain.

### ``Import-csv``

```powershell
# The command import-csv import data to the console
PS C:\Powershell> Import-csv -path daten.csv

Name   Datum      Email          IP-Adresse
----   -----      -----          ----------
Egon   3.1.1999   egon@mail.de   172.120.0.4
Uta    3.1.1999   uta@mail.de    168.130.1.1
Bernd  01.03.2019                156.120.0.3
Paul   04.08.2011 paul@mail.de   10.7.10.1
Marion 06.07.2001 marion@mail.de 172.140.0.1
Otto   04.12.2018 otto@mail.de   198.168.4,200
Anke   31.12.1980                200.100.6.2


PS C:\Powershell>
```
#### Sorting Data

Data can be sorted:

```powershell
#
# Import-CSV -Path daten.csv | Sort-Object -Property { Get-Date $_.Datum }
#
PS C:\Powershell> Import-CSV -Path daten.csv | Sort-Object -Property { Get-Date $_.Datum }

Name   Datum      Email          IP-Adresse
----   -----      -----          ----------
Anke   31.12.1980                200.100.6.2
Egon   3.1.1999   egon@mail.de   172.120.0.4
Uta    3.1.1999   uta@mail.de    168.130.1.1
Marion 06.07.2001 marion@mail.de 172.140.0.1
Paul   04.08.2011 paul@mail.de   10.7.10.1
Otto   04.12.2018 otto@mail.de   198.168.4,200
Bernd  01.03.2019                156.120.0.3
```

#### Filtering Data

Filtering Data by Email - Show all entry where Email is not empty (``$_.Email -ne “” ``)

- -ne = not equal

```powershell
PS C:\Powershell> Import-CSV -Path daten.csv | Where-Object { $_.Email -ne "" } | Sort-Object -Property { Get-Date $_.Datum }

Name   Datum      Email          IP-Adresse
----   -----      -----          ----------
Uta    3.1.1999   uta@mail.de    168.130.1.1
Egon   3.1.1999   egon@mail.de   172.120.0.4
Marion 06.07.2001 marion@mail.de 172.140.0.1
Paul   04.08.2011 paul@mail.de   10.7.10.1
Otto   04.12.2018 otto@mail.de   198.168.4,200
```

The same can be done with the attribute  ``-eq`` = equal:

``` PS
PS C:\Powershell> Import-CSV -Path daten.csv | Where-Object { $_.Email -eq "" } | Sort-Object -Property { Get-Date $_.Datum }

Name  Datum      Email IP-Adresse
----  -----      ----- ----------
Anke  31.12.1980       200.100.6.2
Bernd 01.03.2019       156.120.0.3
```

More about the [Topic](https://docs.microsoft.com/de-de/dotnet/standard/base-types/regular-expression-language-quick-reference "sample title")

Searching CSVs underlies certain rules. The search is always for certain characteristics that are described in a regular expression.
Regular expressions are character strings in which common letters, numbers as well as many special characters are used to describe patterns.

They differs from 5 categories:

- Character class - contains letters or numbers
- Quantifier - defines how often the character class has to repeat
- Anchor - defines start and end of an character class
- round brackets - groups elements
- Escape-Sign - **"\"**  backslash

---

It Is handy to define create a Match-variable for searching.

```powershell
# Match-variable:
$DatumMuster = "\W[0-9]{2}\.[0-9]{2}\.[0-9]{4}\W" 

# angular brackets contain the values that are allowed - [0-9] = any numbers
# curled brackets define the amount of values - {2} = 2 values; {4} = 4 values
# The start and end are define throug \W

PS C:\Powershell> $DatumMuster = "\W[0-9]{2}\.[0-9]{2}\.[0-9]{4}\W"
PS C:\Powershell> (Get-Content -Path daten.csv ) | Foreach-Object {if ($_ -Match $DatumMuster) {$_ }}
Bernd,"01.03.2019",,"156.120.0.3"
Paul,"04.08.2011",paul@mail.de,"10.7.10.1"
Marion,"06.07.2001",marion@mail.de,"172.140.0.1"
Otto,"04.12.2018",otto@mail.de,"198.168.4,200"
Anke,"31.12.1980",,"200.100.6.2"
```

this example show all data that follows "dd.mm.yyyy". The Output does not contain the dates with single letters.

This can be changed:

```PS
$DatumMuster = "\W[0-9]{1,2}\.[0-9]{1,2}\.[1-9]{4}\W" 
```

## Introduction to Powershell Scripts

In Scripts, multiple commands can be stored and executed in a given order.
Windows provides the PowerShell ISE, and development environment for powershell scripts.

### Datatypes and variables

The following Datatypes are avaible in PowerShell:

|Datatype|Meaning|
|---|---|
|int|integer|
|int32|integer (32 Bit)|
|int64+|integer (64 Bit)|
|single|Number with decimal points|
|byte|Byte (8 Bit)|
|char|Character|
|DateTime|Date and Time|
|string| String of characters|

Powershell can automatically decide which datatype to use.

```PS
$value = 123 #will be stored as int
$value = "This is a String" #will be stored string

[int]$sum = 100 + 200 #forcably storing as int
```

### Sequence

The easiest structure of a script is a **sequence**. Single commands are executed one after another.

### Branching

The simplest formof branching are ``if-conditions``.
an if-conditions proves whether a condition is true or false.

### if-else

```powershell
$tp "C:\Powershell"
if (Test-Path $testpfad)
    # if this condition is true
    {Write-Host "The directory $tp exists"}
else
    #if the condition is not true, else is executed
    {Write-Host "The directory $tp does not exist"}
```

### if-else with multiple else-if

It is possible to make an if condition with multiple alternatives:

```powershell
if ($condition = true)
    {instruction 1}
else if ($condition2 = true)
    {intruction 2}
else
    {instruction 3}
```

### switch instructions

Using a switch instruction, multiple conditions are displayed. a switch is recommended if more than 3 conditions are possible.

#### example 1

```powershell
$n = read-host "school note = ?"
switch ($n) {
    "A" {
        $comment = "excellent work!"
    }
    "B" {
        $comment = "good work!"
    }
    "C" {
        $comment = "___ work!"
    }
    "D" {
        $comment = "just enough."
    }
    "E" {
        $comment = "deficiency work!"
    }
    "F" {
        $comment = "not enough."
    }
    default {
        $comment ="no input"
    }
} 
```
#### example 2

```powershell
switch ((Get-Date).Hour) {
    {$_ -ge 6 -and $_ -lt 12}} {$text = "Good Morning!"}
    {...}
}
Write-Host "$text - The time is $(get-date -format HH:mm)"
```

---

### Conditions

|expression|example|meaning|short|
|---|---|---|---|
|z1 -gt z2|[6 -gt 5]| returns true if z1 > z2|greater than|
|z1 -lt z2|[5 -gt 6]| returns true if z1 < z2|less than|
|z1 -ne z2|[5 -gt 6]| returns true if z1 =/= z2|not equal|
|z1 -le z2|[5 -gt 5]| returns true if z1 <= z2|less or equal|
|z1 -ge z2|[5 -gt 5]| returns true if z1 >= z2|greater or equal|
|z1 -eq z2|[5 -gt 5]| returns true if z1 == z2|equal|

### Repetitions - loops

Commands are in dependency to a certain condition executed several times.
A simple loop repeats a command until the the condition is no longer met.
It might be that a while loop is never executed if the condition is not met.

#### while-loop

```powershell
$number = read-host "Enter Number:"

# The while-loop is repeated as long as the entered number is less or equal than 5.
while ($number -le 5) {
    write-host $number
    $number = read-host "Enter Number:"
}
# If a number greater than 5 is entered, the while loop ends.
write-host "The number is greater thatn 5.."
```
#### do-loop

A **do-loop** is at least executed 1 time. At the end of the loop-block a **while** or **until**checks a condition.

##### do-while

If the condition is met, the loop while be executed again.

```powershell
$n = 1
do {
   "Loop nr. $n"
   $n++
}
while ($n -lt 7)
```

##### do-until

If the condition is met, the loop ends.

 ```powershell
$n = 1
do {
   "Loop nr. $n"
   $n++
}
while ($n -ge 7)
```

The two loops do the same, only the condition differs.

#### for-loop

In a for loop the amount of repetitions is defined in the start.

```powershell
for ($n=1; $n -le 6; $n++) {
   "loop nr. $n"
}
```

#### foreach-loop

In a foreach loop the amount of repetitions is defined in a array.

Example 1:

For each city in the citylist, the city is written to the output.

```powershell
$citylist = "Pisa", "Venedig", "Florenz"
foreach ($city in $citylist) {
    write-host $city
}
```

Example 2:

All numbers from 1 to 50 are added to each other.

```PowerShell
$sum=[int]0;
foreach ($n in @(1..50)) {
    $sum += $n
}
write-host $sum
```
Its noteable how the array is written. only the first and last number are declared and seperated by two dots. Such a area is defined with an **@**-sign. 

### Break-Command

Loops continue running until the condition is no longer met. It is possible to break the loop before that happens.
the ``break`` operator stops a running loop.

```powershell
$sum=[int]0;
foreach ($n in @(1..50)) {
    $sum +=$n
    if ($sum -gt 100) { break }
}
 write-host $sum 
```

This loop stops when the ``$sum`` reaches 100.

### Continue-command

With the ``continue`` command a loop is exited and started at the beginning.

```powershell
$n = 0
while ($n -lt 10) {
    $n++
    if ($n -eq 6) {continue}
    Write-Host $n
}
```

This means that in this example, all nubers are written to the output except of number 6.

## Debugging

**Debugging** is the step-by-step execution of a programme. For this purpose, you can have the programme stop at a certain point or execute each step individually.
This is usefull for testing scripts, p.e. if a loop is exited to the wrong condition.

---