# Easy-Wi Update 4.4

## Neuerungen und Änderungen

### Generell

- Wiki mit Handbuch Links ersetzt.
- Globale Belegungsstatistiken werden gelogt und dem Admin dargestellt.
- Easy-Wi Facebook Seite in den Headern verlinkt.
- Überflüssige Fallbacks auf user_language entfernt.
- Nur relevante Steam News werden im User Dashboard angezeigt.
- Liste verfügbarer Dateien für Custom Module wird angezeigt.
- Vertreter können ihre eigenen Daten verwalten.
- Neue PHP Ordnerstruktur.
- PNGs entfernt.
- Social Auth hinzugefügt.

### CMS

- User Prefix auf Nein erlaubt die freie Nickname Wahl beim Registrieren.
- Der HTML Title wird je nach Seite angepasst.

### Game Server

- Mehrere Unterordner sind nun bei Images erlaubt.
- Restart Jobs, werden angelegt, wenn ein Steam Update für as Spiel erfolgt ist.
- Masterserver Ajax aus der settings.php entfernt.
- GameQ aktualisiert.
- Garrysmod Template hinzugefügt.
- Geringere Ram Verbrauch bei der Darstellung von Server Logs.
- Workaround in der statuscheck.php für Spiele mit unterschiedlichen Query Port.
- Nach dem Editieren Redirect zurück zum Restartplaner.
- Workaround für Servercolor/Branding,
- SQL Support für EAC.
- hldsupdatetool entfernt.

### MySQL

- Hosttabellen Verwaltung kann beim User deaktiviert werden.
- Reinstall Funktion hinzugefügt.
- Datenbankgröße wird erhoben und dem User dargestellt.
- Layout Struktur im User Panel den anderen Übersichten angeglichen.

### Root

- Subnet Verwaltung verbessert.
- Root Server IP system überarbeitet.
- Vlan Support hinzugefügt.

### Voice Server

- Bannlisten Funktion im Userpanel.
- Slot- und Traffikverbrauch bei TS3 Servern wird im Userbereich angezeigt.
- Zusätzlich zu Slots, wird auch der Traffik geloggt.

### Webspace

- Webspace/FastDL Modul hinzugefügt.

## Bugfixes

- API: Beim Anlegen von Usern wird kein Passwort gespeichert.
- API: Legacy Verhalten wieder herstellen.
- CMS: Canurl war bei statischen Seiten nicht gesetzt.
- CMS: EasyWi CMS Verlinkung teilweise fehlerhaft.
- Game Server: Popup beim Anlegen einer neuen Datei im WebFTP.
- Game Server: Eigener Game Server Startbefehl.
- Game Server: Minecraft Migration funktioniert nicht.
- Game Server: Game Server Settings Mapgroup Selektion.
- Game Server: Updates starten nicht bei Minute 0.
- Game Server: Der Restart Kalender funktioniert nur für Montag.
- Game Server: downloadPath nicht mit dem Gmeserver Image exportieren.
- Game Server: Protection Mode kopiert keine Datein vom ungeschützten Server.
- Game Server: Online Servers ohne Namen werden als Offline angezeigt.
- Game Server: Game Server wird nicht von der job.php gestoppt.
- Generell: Workaround für Admins ohne eingestellte Zeitzone.
- Generell: Nach frischer Installation werden E-Mails ohne Text gesendet.
- Generell: Redirect enthält doppelte Slashes.
- Voice: TS3 Slots können nach einem Reset bearbeitet werden.
- Voice: Fehlender Include beim Voice Server löschen.