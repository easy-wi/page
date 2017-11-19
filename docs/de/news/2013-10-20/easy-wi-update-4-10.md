## Neuerungen und Änderungen

### Generell

- News Feeds sind standardmäßig aktiviert.
- CMS ist standardmäßig aktiviert.
- Cronjobs können von einem externen Server aufgerufen werden, wenn er whitelisted ist.
- Link in der Versionsübersicht an den neuen Ort des Easy-WI Forums angepasst.
- Passwortfelder werden mit Sternen dargestellt.
- Die News aus dem CMS werden im Dashboard angezeigt.
- Zahlreiche legacy Funktionen entfernt und optimiert.
- Keyfiles können nun mit und ohne die Endung .pub definiert werden.
- Entfernen Buttons mit Kreuz als Icon und roter Darstellung.
- Modul Management hinzugefügt.

### API

- Passwort Hashes werden ebenfalls importiert.

### Benutzer

- Sprachvariablen für Erstell- und Änderungsdatum hinzugefügt.
- Passwörter werden mit PHP 5.5 eingeführten Hash API bzw. einem Fallback gehasht.
- Migration von alten Hashes und aus anderen Systemen importierten Hashes.
- Loginname wird bei Willkommen: (...) angezeigt, wenn kein Familien-, oder Vorname gepflegt wurde.
- Rückgaben, die verraten, ob ein Account existiert, aus dem Passwort Reset entfernt.

### CMS

- Im Falle der Sprachwahl im CMS wird die entsprechende Seite an Stelle der Home Seite angezeigt.

### Game Server

- Root Beschreibung wird beim Anlegen eines Game Server angezeigt und als Fallback die IP.
- Beim Ändern und Anlegen des Masterservers werden die Verbindungsdaten überprüft und nur zugelassen, wenn erfolgreich.
- Multiselect für unterstütze Spiele an Stelle von einem Spiel bzw. ganzem Engine Typ.
- Minecraft Craft Bukkit Startbefehl erweitert.
- l4d, l4d2 und tf2 Images werden mit steamCmd Installer definiert.
- l4d2 und tf2 zum Woraround für appIDs bezüglich API und Updater hinzugefügt.
- Multi Theft San Andreas Image und Query hinzugefügt.
- GTA San Andreas Multiplayer Image und Query hinzugefügt.
- Teeworlds Image und Query hinzugefügt.
- Autoupdater für Minecraft hinzugefügt.
- Autoupdater für Minecraft Craft Bukkit hinzugefügt.
- Im Falle eines Totalverlustes des Roots können alle Game Server mit einem Klick neu erstellt werden.

### MYSQL

- Beschreibung kann bei MYSQL Datenbanken mit angegeben werden.

### Voice Server

- Beim Ändern und Anlegen des Masterservers werden die Verbindungsdaten überprüft und nur zugelassen, wenn erfolgreich.
- Masterserver kann einem Reseller hinzugefügt werden, ohne dass er Verbindungsdaten usw. einsehen kann.

## Bugfixes

- Farben in der Admin Game Serverübersicht.
- Game Leihserver werden nun korrekt beendet.
- Kein Timeout mehr, wenn der TS3 Server den webserver während einer Operation bannt.
- Erstell- und Änderungsdatum wird beim Anlegen des initialen Admin Accounts gesetzt.
- Alte Icon Referenz beim des Userswitches aus der Logübersicht entfernt.
- Rückgabe nach Useraktion im Ticket Bereich des Users korrigiert.
- Validator beim Editieren der eigenen Userdaten korrigiert.
- Veraltete Icons in der Protection Abfrage des CMS ersetzt.
- Leihserverübersicht im CMS wird korrekt dargestellt.
- MYSQL Modul verwaltet die Datenbankuser korrekt.
- Erfolgreiches Anlegen eines Vertreters gibt nun den Erfolg an den User zurück.
- Fehlendes Template admin_voicemasterserver_dl.tpl hinzugefügt.
- Reinstall von Game Servern im Admin Panel korrigiert.
- Startbefehl kann nun das Zeichen # enthalten, welches z.B. für das Forking bei l4d benötigt wird.
- Image ALT der Anzeige vom Protection Mode korrigiert.
- Error Handling der TS3 Klasse für den Fall erweitert, dass keine Serverinfo abgefragt werden konnte.
- Hausnummer kann Querstriche enthalten.
- PHP Notice beim Game Server Reinstall korrigiert.
- Userpanel Game Server Übersicht bezüglich FTP Passwörtern korrigiert.
- FastDL Abgleich startet wieder.
- Gebrauch von $_SERVER in der login.php entfernt.
- Installer definiert das default template.