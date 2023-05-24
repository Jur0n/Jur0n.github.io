---
layout: post
title: How to configure User Desktops
tags: [Desktops, GPO, Active Directory, SERV09F]
category: [Active Directory]
---
## User Profile

### General

Local user profiles are saved to the computer a user signs in. For every user who signs in to a workstation for the first time, a *standard-profile* is generated. Profile folders are saved to the same location: 
`%systemdrive%\Benutzer\<Benutzername>`

### AppData

AppData is a hidden folder and serves as central storage location for userspecific Settings and data. There are 3 Subfolders:

|||
|---|---|
|Local| computerspecific Data and settings, which do not follow the user to an other desktop|
|Roaming|userspecific data and settings which are avaiable to the user through the network|
|LocalLow|Special folder for processes with a low integrity level|

### The Public Folder

`C:\Users\Public`

A public folder for all Users on the workstation.

### Default User

The Folder "Default User" contains predetermined settings on which base new Profilfolders are created 

### Server Stored Userprofile

It is possible to store userprofiles on a server. 
A net-share is needed, which needs to be accessible for all users.
You can determine a profilepath at "AD-Users and -Computer"/ Objectdetails / Profile
`\\<Servername>\<net-sharename>\%username%.`

The are pros and cons of server-stored userprofile:

|Pro|Contra|
|---|---|
|coherent work environment|long loading times for the "sign in" process|
|central storing of data|possible loss of Data|
|easy data restoring||

The cons for server-stored userprofile weight heavier then the pros, and due to this profile storage is determined through GPOs.

### Changing the Win10 Starmenu

The win10 startmenu is tile based. These can be changed by the admin for the users. A sample menu can be created on a local machine, which will then be exported as a .xml file. This file can be set as standard for all users through GPOs.

#### exporting a startmenu

```Powershell
export-startlayout -path C:\Startlayouts\StartlayoutHH.xml 
```

## Group Policy Management 

with group policy an administrator has a mighty tool to get settings to a lot of computers very fast and efficient. 
Nearly every possible Setting on a Windows Server and Desktop can be set in Group Policies.

GPs can be managed under Tools -> Group Policy Management

### Local Safetyguidelines

can be found at `Start/Windows-Verwaltungsprogramme/Lokale Sicherheitsrichtlinie.`

Local verion of GPOs

### Default Domain Policy
 
 The ***Default Domain Policy*** defines fundamental settings that are valid for the whole domain. 
 Its main purpose is the password-policy.

 Even if it seems obvious to make domain wide changes in here, the best pratice would be to not do so.

### Default Domain Controllers Policy

 the ***Default Domain Controllers Policy*** is connected to the **OU** Domain Controllers. 
 Same guidance as for Default Domain Policy, do not make major changes here.

## Policies for user desktops

### Folder Redirection

It is possible to redirect p.e. the user-loved folder `C:\Users\User\Documents` to a server storage location.

To do so go to Grouppolicymanagent and select the OU the folder forwading should be activated for. There, create a new GPO and navigate to `Userconfiguration\Policies\Windows-Settings\Folder Redirection`.
Set the new targetlocation to a network share on a (file)server.

### Win10 Startmenu with GPOs

The startmenu can be defined with a GPO, which makes it standart for the whole Domain. This can be done at `Userconfiguration\Policies\Administrative Templates\startmenue and taskbar`
Here you set a path with is pointing to an exported Menu-configuration.xml file.
The location needs to be an net-share that is accesable by all domain users.
The PS Command for an export is:

```Powershell
export-startlayout -path C:\Startlayouts\StartlayoutHH.xml 
```

Note that after setting the menu with a GPO, the user is not able to make any changes.
To make the user able to make changes in the startmenu, the .xml file can be edited.
`<DefaultLayoutOverride>` needs to be edited with an appedix of:
`LayoutCustomizationRestrictionType="OnlySpecifiedGroups"`

```xml
<DefaultLayoutOverride LayoutCustomizationRestrictionType="OnlySpecifiedGroups"> 
```
This makes the user able to ***add*** custom tiles.

Changes will only apply if you set the last-edited value to a new value:

```Powershell
(ls <path>).LastWriteTime = Get-Date
```

## Group Policies

Windows Server saves information about **Group Policies** at serveral locations.
For explicit indentification a **GUID** is used. 

### GPO

Group policy object
This is the location of the stored group policy.

### GPC

Group policy container
GPOs are stored in GPCs.

### GPT

Group Policy Templates



