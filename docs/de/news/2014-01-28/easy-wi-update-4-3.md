## Ankündigung

Die PECL SSH2 Extension wird nicht länger benötigt!

## Neuerungen und Änderungen

### Generell

- Root Server Menü in Netzwerk und eigentliche Server getrennt
- Zusätzliche Login Methode Key + Passwort
- SSH2 Pecl mit phpseclib ersetzt
- Rote Buttons mit Mülleimer zum löschen
- Zeitzone wird gesetzt, wenn Admin die php.ini nicht konfiguriert
- $dbConnect['debug'] an Stelle von $debug
- REPAIR und OPTIMIZE nur einmal pro Tag
- FTP Klasse statt redundanten Code
- Klasse PHP Mailer für besseren Mail Support

### Game Server

- Asyncronen Web FTP hinzugefügt
- Datei Templates für Game Server
- Catch Exceptions für die GameQ Klasse bei der image.php
- GS Masterupdate aus der reboot.php nach startupdates.php verlagert
- functions_gs.php angelegt
- GameQ aktualisiert
- "Select all" zur DB reparieren Funktion bei GS + Addons hinzugefügt
- Einzigartigkeit von Spielen bei Masterupdate gesichert
- Farbtags werden aus dem Servernamen entfernt
- Rückgabe der reboot.php/startupdates.php verbessert
- Verbessertes Error Handling bei screenlogs
- ESL CS GO Addon hinzugefügt
- Tekkit classic hinzugefügt
- Mehr debugging Debugging Informationen bei der statuscheck.php
- binport beim teeworlds Template
- CSS BHOP Mappackage hinzugefügt
- JSON Support bei Config Support hinzugefügt
- Beim Resync/Reinstall wird Template 1 vorausgewählt
- Starbound Template hinzugefügt
- Maximale Länge für die gamebinary erhöht
- / am Anfang des Import Pfades hinzugefügt
- Gametemplate wird bei Resellern hinzugefügt, wenn es ein Admin bei sich anlegt

### Installer

- Cronjob Timestamps werden in die Zukunft gesetzt
- Beide möglichen Cronjob Einstellungen, per wget und PHP-CLI werden angezeigt
- Versionsüberprüfung wird beim Installer ausgeführt

### Root Server

- Wenn ein Image installiert wird, im Anschluss nur PXE Eintrag und nicht DHCP entfernen

### Benutzer

- Reseller Fix Job hinzugefügt

### Voice Server

- Funktionen aus der class_voice.php entfernt und in functions_voice.php ausgelagert

## Bugfixes

- API defekt durch inkorrekte Validatoren in vorlage.php
- GS Roots Reinstall benutzt falsche ID
- Protectioncheck Formularlink wenn Easy-WI im Unterordner liegt
- Game Server API <installGames> wird ignoriert
- Registrations Aktivierungslink falsch, wenn SEO Links aus sind
- Falsche Rückgabe, wenn Ticket editiert wurde
- Benutzer kann nicht auf Tickets im Status "In Process" antworten
- Spamfilter auf NEIN, wird ignoriert
- Installer nutzt nicht existierende Sprache als Fallback
- Cronjob Timestamps werden für Reseller nicht aktualisiert
- Kein Error Handling wenn die keyfile fehlt
- Multiple falsche Texte im Installer verwendet
- install.php: Undefined index: USER
- +1 Slot beim GS Check hinzufügen, wenn SourceTV aktiv ist
- Fehler im Leihserver Modul
- Veraltete SQLs werden im TS3 Importer benutzt
- Initiales Passwort wird während des Imports nicht gesetzt.
- implode(): Invalid arguments userpanel_gserver.php
- Undefined index: active at statuscheck.php
- Include für queries.php
- benutzernamen beim TS3 Importer
- Korrekete Abhängigkeiten, wenn das Default Addon angelegt/korrigiert wird
