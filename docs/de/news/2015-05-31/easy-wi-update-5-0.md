## Wichtig

Durch den Verzicht auf die control.sh und das optionale Verwenden von Quotas muss die /etc/sudoers wie folgt erweitert werden. Dabei sind die Quotas bezogenen Einträge optional:

```sh
easywi ALL = NOPASSWD: /usr/sbin/useradd
easywi ALL = NOPASSWD: /usr/sbin/userdel
easywi ALL = NOPASSWD: /usr/sbin/deluser
easywi ALL = NOPASSWD: /usr/sbin/usermod
easywi ALL = NOPASSWD: /usr/sbin/setquota
easywi ALL = NOPASSWD: /usr/sbin/repquota
easywi ALL = (ALL, !root:easywi) NOPASSWD: /home/easywi/temp/*.sh
```

Je nachdem, wie ihr den Masteruser genannt habt, muss "easywi" durch euren Namen ersetzt werden.

## Änderungen

### API

- TSNDS API hinzugefügt
- Aussagekräftigere Fehlermeldung bei Zugang verweigert
- Rückgabe der gesendeten Operation für besseres Debugging
- Daten werden bei der Edit Operation vollständig zurück gegeben
- IP wird beim Add/Edit von Game und Voice Servern zurück gegeben
- Game Switch Spiele können bei Edit Operation hinzugefügt und gelöscht werden
- FTP User wird bei Game Servern zurück gegeben
- Das initiale Passwort kann bei Game Servern gesetzt werden
- Der Core Count wird bei Game Servern zurück gegeben
- Liste aller installierter Game Typen/Master Apps
- Liste aller Masterserver mit optionalen Limit
- Multiple Master IDs können in allen Add Operationen verwendet werden
- Beschreibung wird bei Master Listen zurück gegeben
- Webspace Master Liste kann angezeigt werden
- MySQL Master Liste kann angezeigt werden
- Generierter Benutzername wird zurück gegeben, wenn keiner gesendet wurde
- User Liste kann angezeigt werden
- Neue Methode clean User externalID

### CMS

- hreflang Unterstützung
- index.php wird nach Home im Seo Mode geroutet
- WYSIWYG Editor Summernote beim Seiten und News Management

### Feeds

- Externe News des Feeds werden ebenfalls eingelesen
- Bilder werden aus dem Feed entfernt

### Game Server

- Quota Support
- Multiple Festplatten werden unterstützt
- SteamCMD Login kann pro Template/Image gepflegt werden
- control.sh durch PHP Klasse ersetzt
- Konfiguration der control.sh durch App Server Konfiguration ersetzt
- Protected Linux System User wird nur angelegt, wenn der Modus generell für den Game Server verfügbar ist
- SteamCMD Updates werden nacheinander ausgeführt
- Option [no_padding] für optionale Startbefehle bei Addons
- Query Port kann im Template definiert werden
- Neues Template No More Room in Hell
- Neues Template Project Cars
- FTP Server ohne Chroot werden unterstützt
- Support des Verleihs von Minecraft, Samp und Teeworlds
- Statuscheck.php Timeout erhöht
- Restart durch einen Cronjob wird mit der IP 127.0.0.1 geloggt
- "@" und "." im FTP Usernamen beim FastDL zulässig

### Generell

- Neues Admin/User Template in 6 Farben
- Große Teile des Codes refactored
- Angelege Prozesse nur noch in einem Schritt
- SSH IPs können ausschließlich für den Connect verwendet werden (DMZ)
- Icon und Text des Headers in den Einstellungen konfigurierbar
- Statusseite für Cronjobs und PHP Extensions
- Third party CSS, JS und Fonts werden mitgeliefert
- Query Resultate werden mit while an Stelle von foreach geloopt umd Ram Verbrauch zu senken
- Modul Konzept aktualisiert und robuster gestaltet
- Unterstützzung von CURRENT_TIMESTAMP bei der Tabellen Reparieren Funktion
- Benutzer kann Info Texte deaktivieren
- Charakter "-" kann bei Passwörtern benutzt werden
- Default externalID ist nun "leer"
- Job Einträge werden geschrieben um alles zu stoppen, wenn User deaktiviert oder gelöscht wird
- Verbesserte Fehler Meldungen bei External Auth

### MySQL

- externalID für Datenbanken verwaltbar

### Tickets

- HTML5 Validierung hinzugefügt um 404 Fehler zu vermeiden

### Voice Server

- externalID zu TSNDS hinzugefügt
- Maximale TSNDS Menge am Master einstellbar
- Beschreibung kann bei Voice Mastern gepflegt werden

### Webspace

- Domains können Webspace zugeordnet werden
- Frei definierbare optionale php.ini Konfiguration

### Third Party

- DataTables hinzugefügt
- Chosen hinzugefügt
- moment.js hinzugefügt
- Daterange Picker hinzugefügt
- Bootstrap aktualisiert
- Font Awesome aktualisiert
- HybridAuth aktualisiert

## Bugfixes

- Validator Klasse und multidimensionale Arrays
- Installer wirft einen Fehler bei falschen MySQL Daten
- Nur eine Zeitquelle bei der lend.php
- External Auth benutzt falschen SSL Port
- SSL/TLS Support beim PHPMailer
- Custom Colums
- Bcrypt Support wird in jedem Fall überprüft
- Prefix beim User Anlegen als Reseller ignoriert
- Voice Master mit externem TSDNS Master
- Ungültiger Wert für next free in der Verleih API
- PHP Notice Meldungen bei gestopptem Voice Server
- MySQL Übersicht benutzt falschen Index
- SQL Exception bei API MySQL DB Edit
- TSDNS Key Login funktioniert nicht
- Http Server startet nicht nach Edit
- E-Mail Template von Useradd und Registration nicht zu bearbeiten
- DB Dump kann nicht gedownloaded werden