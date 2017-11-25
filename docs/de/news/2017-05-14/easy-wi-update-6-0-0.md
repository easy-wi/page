# Easy-Wi Update 6.0.0

## Hinweis

Nach dem Update ist auf jedem Root Server mit Game Servern das Migration Skript auszuführen:
[https://github.com/easy-wi/server/blob/master/migrate.sh](https://github.com/easy-wi/server/blob/master/migrate.sh)

## Änderungen

### General

- Hybrid Auth auf 2.9.5 aktualisiert
- Support von Ubuntu 16.04
- Russische Sprache hinzugefügt
- Globale Suche entfernt
- Admins werden bei veralteter Easy-Wi Installation informiert
- Länge der Namen von Public Keyfiles global auf 255 erhöht
- Versionierung über GitHub an Stelle von easy-wi.com

### CMS

- Download Modul kann externe Downloads verwalten
- HTTP Only wird bei https gesetzt

### Game Server

- ip_port Unterordner entfernt
- Workaround -nobreakpad bei CS:GO Template
- GameQ auf die neueste Version aktualsiert
- Server wird vor Reinstall gestoppt
- Project Cars Template angepasst
- Sonderzeichen @ kann bei Addon Ordnern angeben werden
- Backup Erstellen wird ignoriert, wenn bereits eines läuft
- Server wird gestoppt, bevor der Umzug gestartet wird
- Beschreibung des Servers kann verwaltet werden
- Fast Download Anweisungen für UnrealEngine hinzugefügt
- Steam Server und Game ID nun beide konfiguriertbar

### Voice Server

- Token können beim Anlegen über API übergeben werden
- Inifile wird beim Restart angegeben
- Beschreibung des Servers kann verwaltet werden

### Web

- PHP-FPM Support hinzugefügt
- Default Redirects in den standard Templates

### MySQL Server

- MySQL Server 5.7 Unterstützung hinzugefügt
- MySQL Master Beschreibung kann verwaltet werden

### Installer

- Developer und Stable Release Train auswählbar

## Bugfixes

### General Bugs

- Glyphicons definiert, aber nicht verfügbar
- Updater von 5.22 auf 5.30 fehlerhaft bei mehrfachem Aufruf
- Variable feedArray in der Admin Home Ansicht undefined in manchen Fällen
- Custom Modules werden in der User Ansicht nicht korrekt ins Menü eingebunden
- Zu Kurzes Passwort des API Users kann API unbrauchbar machen
- Vertreter wird nicht korrekt gegrüßt
- Admin kann auf User zugreifen, für die er keine Berechtigung hat
- SQL Fehler beim Update von mit md5 Hash importierter User
- Redirect nach Logout auf System ohne Domain funktioniert nicht

### CMS Bugs

- Summernote Editor funktioniert nicht bei Seiten und News
- News bearbeiten und Keyword entfernen zur gleichen Zeit geht nicht
- User Aktivation Link
- Leih Server funktionieren nicht bei deaktierten SEO URLs

### Game Server Bugs

- FTP Connect beim Serverlog fehlerhaft dargestellt
- Sperren von CVARs in mehreren Dateien funktioniert nicht
- Lange INI Dateien werden abgeschnitten
- API FTP Passwort Änderung wird nicht auf den Root übertragen
- Italienische Übersetzung bei Monsta FTP
- Typo bei Game Server Update Mail
- Typo bei Master Server Menu Eintrag
- Shorten mit Nummer am Anfang crashen API
- Upload von leeren Dateien via MonstaFTP nicht möglich
- Kopie der Configs beim Protection Mode funktioniert nicht

### Voice Bugs

- Erstellen via API schlägt fehl
- SSH Keys beim Master funktionieren nicht
- SSH Keys mit Passwort beim TSDNS Master funktionieren nicht
- Reset von notified beim Statuscheck schlägt fehl
- API TSDNS Löschen funktioniert nicht
- Masterid beim Reimport nicht gesetzt
- Typo bei Voice Master veraltet Mail
- Suhosin check beim Import auf Systemen ohne, löst Fehler aus
- Fehlerhafte Fehlermeldungen beim Connection Check
- Versions Lookup bei nicht existierendem Mirror entfernt

### Web Bugs

- SSH Keys beim Master funktionieren nicht
- Angabe von URLs im Vhost Template nicht möglich

### User Bugs

- API User Liste funktioniert im Debug Mode nicht

### Installer Bugs

- Single Quotes bei Einträgen für die config.php lösen Syntax Fehler aus
- User Passwort Validation nicht vorhanden
- Valides Passwortformat wird abgelehnt
- Undefined Variable ui
