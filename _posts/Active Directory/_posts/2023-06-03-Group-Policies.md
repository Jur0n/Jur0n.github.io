---
layout: post
title: Group Policies (GPOs)
tags: [GPO, Active Directory, SERV10F]
category: [Active Directory]
---

# Group Policies

## General Information

### Different Layers of Group Policies

1. local Policies
2. GPOs on Domain level
3. GPOs on OU level
4. GPOs on location level

### Restoring of the standard group policies

If something went wrong while editing the standard group policies, it is possible to restore the installation-standard of the group policies.
For That, `dcgpofix.exe` can be used.

```powershell
dcgpofix [/ignoreschema] [/target:{domain | dc | both}]
```

`/ignoreschema` with this parameter the version number of the AD-Schema is ignored.

`/target` defines which GPO shall be restored:
- `domain`: Default Domain Policy
-  `dc`: Default Domain Controllers Policy
-  `both`: both standard policies

### Administrative Templates

Administrative Termplates are special filex which describe the structure of Policies. A lot of Templates come with Windows Server, but additional Templates for p.e Microsoft Office can be added. There are language neutral versions of templates and the Language specific addons.

| GP-Template|Location |
|---|---|
|ADMX-Dateien (lokal)|`%systemroot%\PolicyDefinitions`|
|ADML-Dateien (lokal)|`%systemroot%\PolicyDefinitions\[language]`|
|ADMX-Dateien (Domäne)|`%systemroot%\SYSVOL\domain\policies\ PolicyDefinitions`|
|ADML-Dateien (Domäne)|`%systemroot%\SYSVOL\domain\policies\ PolicyDefinitions\[language]`|

Templates should always be stored at the central location, which is:
`%systemroot%\SYSVOL\domain\policies\PolicyDefinition`
by doing so it can be guaranteed that they are replicated.

## Configuration of Group Policies

Group Policies can exist on different levels.

With **Userconfiguration** policies are defined on an user-level

With **Computerconfiguration** policies are defined on a computer-level.

Both branches contain mostly the same policies, but may differ in some points.
Any configuration done in **Computerconfiguration** has priority to the same configuration in **Userconfiguraion**.

### Inheritance of Policies

GPOs **inherit** to subsidary OUs and containers. It is activated by default, but can be *deactivated* for an OU.
Another possibillity is to **enforce** Policies, which can be set in an GPO. By doing so it can be guaranteed that all subsidary OUs get the Policy, even if they are managed by another administrator.

### Different Status of GPOS:

|Status|explanation|
|---|---|
|active|The GPO is applied |
|not configured| The GPO is inherited by an subordinate OU and is applied through it|
|deactivated|The GPO is not applied|

### gpresult

The commandline tool `gpresult` displays the applied GPOs to an object.

```cmd
gpresult 
[/ s <Computer> [/ u [<Domain> \] 
Benutzername [/ p [<Password>]]]] 
[/ user[<TargetDomain> \] <TargetUser>] 
[/ scope (user | Computer)] 
[/ r |/v |/z] [[/ x |/h] Dateiname [/ f]]
```

| Syntax|Explanation|
|---|---|
|`/s   Computer`|Specifies the name or IP address of a remote computer.<br>(Do not use backslashes.) The default is the local computer.|
|`/u   Domain \ User`|Runs the command with the account permissions of the user that is specified by<br>User or Domain\User. The default is the permissions of the current logged-on<br>user on the computer that issues the command.|
|`/p   Password`|Specifies the password of the user account that is specified in the /u parameter.`|
|`/user   TargetUserName`|Specifies the user name of the user whose RSOP data is to be displayed.`|
|`/scope { user | computer }`|Displays either user or computer results. Valid values for the /scope parameter are user or computer. If you omit the /scope parameter, gpresult displays both user and computer settings.|
|`/v`|Specifies that the output display verbose policy information.|
|`/z`|Specifies that the output display all available information about Group Policy.<br> Because this parameter produces more information than the /v parameter,<br> redirect output to a text file when you use this parameter<br> (for example, gpresult /z >policy.txt).|
|`/?`|Displays help at the command prompt.|
