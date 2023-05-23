---
layout: post
title: Usefull GPOs
tags: [Desktops, GPO, Active Directory, SERV09F]
category: [Active Directory]
---

This Blog article is a collection of usefull GPOs

## GPOS recommended by my studies

Betrachten Sie daher die folgenden Einstellungen als ausbaufähigen Vorschlag in beide Richtungen:

Windows Explorer

Richten Sie für Benutzer den Windows Explorer mit den folgenden Vorgaben ein. Lesen Sie hier jeweils in den Erläuterungen, auf welche Version des Betriebssystems sich die Richtlinie bezieht! 
Sie finden die Richtlinien unter Benutzerkonfiguration/Richtlinien/Administrative Vorlagen/Windows-Komponenten/Datei-Explorer:

- Da sowieso nur ein Administrator den Computer verwalten können soll, sollten Sie Den Menüeintrag „Verwalten“ im Windows Explorer-Kontextmenü ausblenden.
- Mit der gleichen Begründung können Sie die Registerkarte „Hardware“ entfernen.
- Wenn Sie verhindern möchten, dass die Benutzer interne Daten auf CDs brennen, können Sie die CD-Brennfunktionen entfernen.

So können Sie Startmenü und Taskleiste unter Windows 8 konfigurieren:
- Wenn Sie dem Benutzer nicht erlauben möchten, Programme als ein anderer Benutzer auszuführen, deaktivieren Sie Benutzerkonfiguration/Richtlinien/Administrative Vorlagen/Startmenü und Taskleiste/Befehl „Als anderer Benutzer ausführen“ in „Start“ anzeigen.
- Störende Benachrichtigungen auf der Kacheloberfläche deaktivieren Sie über Benutzerkonfiguration/Richtlinien/Administrative Vorlagen/Startmenü und Taskleiste/Benachrichtigungen/Kachelbenachrichtigungen deaktivieren.
- Veränderungen im Bereich „Start“ verhindern Sie durch Benutzerkonfiguration/Richtlinien/Administrative Vorlagen/Startmenü und Taskleiste/Deinstallieren von Anwendungen aus „Start“ durch Benutzer verhindern.
-  Unser Klassiker: Menüeintrag „Ausführen“ aus dem Menü „Start“ entfernen.

Im Bereich Desktop aktiveren Sie die folgenden Richtlinien:

Der Zugriff auf die Systemsteuerung kann unter Benutzerkonfiguration/Richtlinien/Administrative Vorlagen/Systemsteuerung/Angegebene Systemsteuerungssymbole ausblenden geregelt werden.
Deaktivieren Sie z.B. die folgenden Icons: Benutzerkonten, Datum und Uhrzeit, Energieoptionen, Gamecontroller, Geplante Tasks, Hardware, Internetoptionen, Netzwerkverbindungen, Scanner und Kameras, Schriftarten, Software, Sounds und Audiogeräte, Sprachein-/-ausgabe, System, Telefon- und Modemoptionen, Verwaltung.

Im Bereich Benutzerkonfiguration/Administrative Vorlagen/System können Sie mithilfe der Richtlinien Nur zugelassene Windows-Anwendungen ausführen bzw. Angegebene Windows-Anwendungen nicht ausführen Positiv- bzw. Negativlisten der erlaubten/verbotenen Programme erstellen.
Dies ist aber ein sehr mühsames Unterfangen, zumal Sie sehr wahrscheinlich diese Listen oft überarbeiten müssen. Es ist daher die Frage, ob sich der Aufwand lohnt oder ob es nicht ausreicht, zusätzlich zu der Richtlinie Befehl „Ausführen“ aus dem Startmenü entfernen noch die Richtlinien Zugriff auf Eingabeaufforderung verhindern und Zugriff auf Programme zum Bearbeiten der Registrierung verhindern zu aktivieren.
In diesem Zusammenhang sollten Sie natürlich auch den Zugriff auf die PowerShell verhindern. Hierzu müssen Sie dieses Programm in die Liste der verbotenen Windows-Programme aufnehmen.

---