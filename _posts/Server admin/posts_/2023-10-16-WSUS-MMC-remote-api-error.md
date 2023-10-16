---
layout: post
title: WSUS MCC Remote connectio API error
tags: [WSUS, windows,]
category: [Server admin]
---

# WSUS MCC Remote connectio API error

The following error Message appears in the WSUS MMC:

`` Die WSUS-Verwaltungskonsole konnte über die Remote-API keine Verbindung mit dem WSUS-Server herstellen.``

These steps worked as solution:

1. 2GB Memory sind eindeutig zu wenig. Ich würde der Maschine min. 16GB geben.
2. Das von Joe weiter vorne im Thread angesprochene "Verschlucken" des Servers, solange er die Erstsynchronisierung macht. Diesen Effekt gibt es glaube ich schon seit es den WSUS gibt. Du könntest da nach seiner Beschreibung vorgehen und das Synchronisieren häppchenweise machen.
3. Die im oben angegebenen Link behandelte PrivatMemory Knappheit des IIS. Hier auf 8GB erhöhen.
Ich denke, dann wird auch Dein WSUS laufen.

Da es in dem verlinkten Thread nicht beschrieben wird, wie man das PrivatMemory im IIS erhöht, möchte ich das der Vollständigkeit halber hier noch gerne machen:
Vom Servermanager aus wird unter Tools der Internetinformationsdienste (IIS)-Manager aufgerufen.
Dort dann in der linken Fensterhälfte (evtl. erweitern) den Punkt Anwendungspool anklicken. Daraufhin wird in der rechten Hälfte eine Liste der Anwendungspools angezeigt. Hier den WsusPool auswählen und mit der rechten Maustaste anklicken. Im Kontextmenü dann "Erweiterte Einstellungen ..." wählen.
Im sich öffnenden Fenster dann ganz nach unten scrollen und unterhalb von "Wiederverwendung" dann das Limit für den privaten Speicher von Hand auf 8000000 KB setzen. Mit OK bestätigen und damit ist es schon fertig. Ich habe den Server noch neu gestartet. Ob das nötig gewesen wäre, weiß ich nicht. Darum gebeten hat er nicht.