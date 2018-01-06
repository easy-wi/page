# Easy-Wi Update 6.0.4

## Änderungen

### General

- IPv6 Addressen können nun geloggt werden
- Diverse Verbesserungen im italienischen Sprachpacket

### Game Server

- GameQ Query Libary aktualisiert
- Start/Stop Button bei der Konsole im Benutzerbereich hinzugefügt
- Workaround für Debian 9 und screen -L hinzugefügt
- CSV Dateien werden nun kopiert

## Bugfixes

- Name des Spiels wird nicht in der Konsole bei der statuscheck.php angezeigt
- Game Server Status Zeitstempel in der Benutzer Übersicht
- Bei DB Entfernen von Game Servern wird der Shell Debug Output angezeigt
- Beim Neustart von Game Server und fehlender geschützter Datei wird dir Ordnerstruktur rekusiv noch einmal erstellt
- Der "Notified count" wird nicht zurück gesetzt sobald ein Game Server wieder erreichbar ist
- Update Success wird bei SteamCMD Spielen nicht mehr korrekt erkannt
- Restart Planer funktioniert nicht mit neuestem MySQL auf Ubuntu 16.04
- ARK Template
- MTA:SA Template
- Seiten Liste funktioniert nicht auf neuesten MySQL Server mit Ubuntu 16.04
- CMS Settings nicht immer editiertbar
- Gehört ein TS3 Masterserver einem Reseller wird der Status nicht korrekt abgeprüft
- Initiales TS3 Passwort wird nicht in der DB gespeichert
- suhosin check beim Import von TS3 Servern
- Falsche Überschrift in der TSDNS Admin Übersicht
- Gruppen Anlegen mit aktiviertem Debugger funktioniert nicht
- Diverse undefined Variablen Notices
- Falsches Icon von Font Awesome bei Hybridauth für Twitch benutzt
- Security Problem beim Switch vom Reseller zu Benutzern
- SQL Syntax bei Game und Voice Server API mit External ID
- Login Loop (Erster Login kann fehl schlagen)
- "Please allow redirection settings" bei Logout und einigen Server Konfigurationen
- Ticket Kategorie kann auf neuesten MySQL Server mit Ubuntu 16.04 nicht angelegt werden
- Redirect im Default Apache2 Vhost Template