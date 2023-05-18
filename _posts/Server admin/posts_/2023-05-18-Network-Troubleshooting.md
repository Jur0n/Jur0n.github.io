---
layout: post
title: Network troubleshooting
tags: [cmd, ipconfig, ip, network, windows, nslookup]
category: [Server admin]
---

## ipconfig

### Syntax

```cmd
ipconfig [/allcompartments] [/all] 
[/renew [<adapter>]] [/release [<adapter>]]
[/renew6[<adapter>]] [/release6 [<adapter>]]
[/flushdns] [/displaydns] [/registerdns]
[/showclassid <adapter>]
[/setclassid <adapter> [<classID>]]
```

| Parameter|definition |
|---|---|
|/all | Displays the full TCP/IP configuration for all adapters. Adapters can represent physical <br> interfaces, such as installed network adapters, or logical interfaces, such as dial-up connections. |
|/displaydns |  Displays the contents of the DNS client resolver cache|
|/flushdns | Flushes and resets the contents of the DNS client resolver cache |
|/registerdns | Initiates manual dynamic registration for the DNS names and IP addresses that<br>are configured at a computer. |
|/release `[<adapter>]`| Sends a DHCPRELEASE message to the DHCP server to release the current DHCP configuration<br> and discard the IP address configuration for either all adapters (if an adapter is not specified)<br> or for a specific adapter if the adapter parameter is included. |
|/renew `[<adapter>]`| Renews DHCP configuration for all adapters (if an adapter is not specified) or for a specific<br> adapter if the adapter parameter is included. |
|/showclassid `<adapter>`|Configures the DHCP class ID for a specified adapter. To set the DHCP class ID for all<br> adapters, use the asterisk (*) wildcard character in place of adapter.|
|/setclassid `<adapter>`<br>`[<classID>]`|Displays the DHCP class ID for a specified adapter. To see the DHCP class ID<br>for all adapters, use the asterisk (*) wildcard character in place of adapter.|

[ipconfig - Microsoft Learn Article](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ipconfig)

---

## ping

### Syntax
---

```cmd
ping [/t] [/a] [/n <count>] [/l <size>] [/f]
[/I <TTL>] [/v <TOS>]
[/r <count>] [/s <count>] 
[{/j <hostlist> |/k <hostlist>}] [/w <timeout>]
[/R] [/S <Srcaddr>] [/4] [/6] <targetname>
```

|Parameter|Definition|
|---|---|
|/t|Specifies ping continue sending echo Request messages to the destination until interrupted. To interrupt and display statistics, press CTRL+ENTER. To interrupt and quit this command, press CTRL+C.|
|/a|Specifies reverse name resolution be performed on the destination IP address. If this is successful, ping displays the corresponding host name.|
|/n `<count>`|Specifies the number of echo Request messages be sent. |
|/l `<size>`>|Specifies the length, in bytes, of the Data field in the echo Request messages.|
|/v `<TOS>`|Specifies the value of the Type Of Service (TOS) field in the IP header for echo Request messages sent (available on IPv4 only). The default is 0. TOS is specified as a decimal value from 0 through 255.|
|/r `<count>`|Specifies the Record Route option in the IP header is used to record the path taken by the echo Request message and corresponding echo Reply message (available on IPv4 only). Each hop in the path uses an entry in the Record Route option. If possible, specify a count equal to or greater than the number of hops between the source and destination. The count must be a minimum of 1 and a maximum of 9.|
|/s `<count>`|Specifies that the Internet timestamp option in the IP header is used to record the time of arrival for the echo Request message and corresponding echo Reply message for each hop. The count must be a minimum of 1 and a maximum of 4. This is required for link-local destination addresses.|
|/j `<hostlist>`|Specifies the echo Request messages use the Loose Source Route option in the IP header with the set of intermediate destinations specified in hostlist (available on IPv4 only). With loose source routing, successive intermediate destinations can be separated by one or multiple routers. The maximum number of addresses or names in the host list is 9. The host list is a series of IP addresses (in dotted decimal notation) separated by spaces.|
|/k `<hostlist>`|Specifies the echo Request messages use the Strict Source Route option in the IP header with the set of intermediate destinations specified in hostlist (available on IPv4 only). With strict source routing, the next intermediate destination must be directly reachable (it must be a neighbor on an interface of the router). The maximum number of addresses or names in the host list is 9. The host list is a series of IP addresses (in dotted decimal notation) separated by spaces.|
|/w `<timeout>`|Specifies the amount of time, in milliseconds, to wait for the echo Reply message corresponding to a given echo Request message. If the echo Reply message is not received within the time-out, the "Request timed out" error message is displayed. The default time-out is 4000 (4 seconds).|
|/R|Specifies the round-trip path is traced (available on IPv6 only).|
|/S `<Srcaddr>`|Specifies the source address to use (available on IPv6 only).|

