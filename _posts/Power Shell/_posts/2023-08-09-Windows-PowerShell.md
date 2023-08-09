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




