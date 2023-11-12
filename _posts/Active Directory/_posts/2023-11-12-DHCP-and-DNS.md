---
layout: post
title: DHCP & DNS   
tags: [DHCP, DNS, Active Directory, SERV13F]
category: [Active Directory]
---

# DNS

## DNS-Zones

A zone is coherent area of the domain namespace for which a DNS server is authorising. The DNS server has authorisation for nameresolving in this zone.
All DNS Clients of a zone are registered with their IP-address at the DNS-server for which they are configured.
A DNS server "knows" all clients of his zone(s). It can assignments with ip-addresses and the hostnames of the devices.

A zone can hold multiple Domains and subdomains.
There are 3 types of uones with different properties.

### Primary Zone

A primary zone is characterised through a zone file, in which can be written to and read from. This file is a standart text file.
DNS client can register to a primary zone.
All changes made to the zone (re- and unregistering of clients) are saved to the zone file.
If a new zpne is created on a DNS server, is has to be a primary zone.
The zone-file is stored at `%systemroot%\system32\dns` (Windows Server).

### Secondary Zone

A secondary zone is characterised through a not read-only zonefile, which is also saved as textfile.
All changes made to the primary zone are savedto the primary zonefile and are replicated to the secundary zonefile. A sekundary zone is created to copy an existing zone and its zonefile.
With the use of this, network and server load can be reduced.

### Stubzone

A forward-lookup zone can also be konfigured as stubzone. A Stubzone contains partial quantities of zonedata and a copy of Resource records, which are required to indentify the authorising DNS-Server in an zone.
A Stubzone saves a copy of a zone, which does only contain **Nameserver** (NS), **start of authority**(SOA) and **A-Entrys**. The NS-Resourcerecord allocates the DNS-domainnames to servers that are authorized or contains a zonefile for the domain.
The SOA-Resourcerecord provides the startingpoint of information saved in a zone.

### Active Directory-integrated Zone

In this zone, the zone information is stored in AD-structure and not as a textfile. Updates take place automatically through AD-replication. For this, all DNS servers have to installed at Domain Controllers.
This option is recommended because it simplyfies administrative tasks.

## Resource records

A zoenfile stores information that is needed by the DNS-server for nameresolving. This information is stored as Resource records. 
Resource records are Databaseentries which have several attributes like Hostname, IP-address or Hostname of a device.

A DNS-Forward-Lookupzone contains different resource records:

-   Host- and address records (A)
-   Server records (SRV)
-   Mail-Exchange records (MX)
-   Alias (CNAME)

|Resource Record|Definition|
|---|---|
|A|The **A**dress record contains the allocation of an Hostname and it´s IP-address|
|CNAME|The **C**anonical **Name** is a second record for a device. A second Hostname can be allocated to an IP-address, p.e. www for a webserver |
|HINFO|Contains **Info**rmation about DNS-**H**ardware and -software. p.e. Processor and operating system|
|MX|The MX record identifies a Mailserver. Mulitple records are possible.|
|NS|The NS record identifies the **N**ame-**S**erver, the DNS-server. Primary and secondary DNS-server are registered.|
|PTR|The **Pointer** record is used for reverse nameresolving, IP to Hostname. This record is used for reverse-lookupzones.|
|SOA|The SOA record provides the startingpoint of information saved in a zone. (**Star of Authority**)|
|SRV|the **Server** record marks a service that is executed on a host. If a host hat to authenticate at a DC, it is looking for a SRV record.|


