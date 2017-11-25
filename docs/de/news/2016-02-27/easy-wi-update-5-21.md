# Easy-Wi Update 5.21

## Änderungen

### CMS

- Liste von Sub Pages im Page Template verfügbar

### Game Server

- Restart nach Update kann deaktiviert werden
- Benutzer kann Auto Restarts deaktivieren
- JSON kann über den Web FTP editiert werden
- RAM wird bei der Server Belegung berücksichtigt
- Live Console mit Monospace Font
- Passiv FTP wird unterstützt

### Voice Server

- Standard Wert für connectIpOnly gesetzt
- Flex Slots Konfiguration ausgeblendet

### MySQL

- Mehr Fehler Details im MySQL DB CRUD
- Mehr Standard Werte bei MySQL Master hinzufügen gesetzt

## Bugfixes

- GS können nicht editiert werden, wenn der Root voll belegt ist
- Alle GS eines Roots werden nach irgend einem Update neu gestartet
- HDD Wert wird bei der GS API nicht übergeben
- GS Restart funktioniert unter besonderen MC Umständen nicht immer
- GS Backups haben deploy Probleme
- Zu viele Dateien beim GS sync kopiert
- GS Backups werden beim Restart gelöscht
- Configs werden bei manchen GS Templates zweimal gelistet
- Regex wird bei GS config edit nicht immer escaped
- MySQL Master Passwort ist Typ Text
- MySQL hinzufügen/mod behandelt external SQL Fehler nicht
- Falsche Templates beim Page CRUD gesetzt
- Page Edit setzt Variable naviDisplay nicht
- Page Keywords Löschen funktioniert unter manchen Umständen nicht
- PHP Config beim Web Master wird nicht angezeigt
- Maximale Voice Backups können nicht größer als 9 gesetzt werden
- Neueste TS3 Version kann nicht erfasst werden
- Voice API konvertiert JSON Config nicht
- Falsche Success Anzeige beim Job Log
- E-Mail Umlaute und Anordnung
- Web Master Auswahl
- Web Quota bei mehreren Partitionen