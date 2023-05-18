---
layout: post
title: Network troubleshooting
tags: [cmd, ipconfig, ip, network, windows, nslookup]
category: [Server admin]
---

## ipconfig

The command **``ipconfig``** is one of the most usefull for networkadministrators.

### Syntax

```cmd
ipconfig [/allcompartments] [/all] [/renew [<adapter>]] [/release [<adapter>]] [/renew6[<adapter>]] [/release6 [<adapter>]] [/flushdns] [/displaydns] [/registerdns] [/showclassid <adapter>] [/setclassid <adapter> [<classID>]]
```

| Parameter|definition |
|---:|---|
|/all | Displays the full TCP/IP configuration for all adapters. Adapters can represent physical interfaces, such as installed network adapters, or logical interfaces, such as dial-up connections. |
|/displaydns |  Displays the contents of the DNS client resolver cache|
|/flushdns | Flushes and resets the contents of the DNS client resolver cache |
|/registerdns | Initiates manual dynamic registration for the DNS names and IP addresses that are configured at a computer. |
|/release `[<adapter>]`| Sends a DHCPRELEASE message to the DHCP server to release the current DHCP configuration and discard the IP address configuration for either all adapters (if an adapter is not specified) or for a specific adapter if the adapter parameter is included. |
|/renew `[<adapter>]`| Renews DHCP configuration for all adapters (if an adapter is not specified) or for a specific adapter if the adapter parameter is included. |
|/showclassid `<adapter>`|Configures the DHCP class ID for a specified adapter. To set the DHCP class ID for all adapters, use the asterisk (*) wildcard character in place of adapter.|
|/setclassid `<adapter> [<classID>]`|Displays the DHCP class ID for a specified adapter. To see the DHCP class ID for all adapters, use the asterisk (*) wildcard character in place of adapter.|

[Microsoft Learn Article](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ipconfig)

## ping


