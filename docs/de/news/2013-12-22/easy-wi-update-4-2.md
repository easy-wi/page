# Easy-Wi Update 4.2

## Neuerungen und Änderungen

### Generell

- Benutzer, Vertreter, Game Server und Voiceserver importer hinzugefügt
- Datenbank Menü um die Funktionen Game- und Addon Reparieren erweitert
- Erster Menüeintrag von "Dashboard" zu "Home" umbenannt.
- CMS und Lendserver active/inactive ins Modul Management ausgelagert.
- Neuer Web Installer
- Verbesserte template Header
- Verbesserte Easy-WI Settings Verwaltung
- Verbesserte Impressum Verwaltung
- Bootstrap wird über ein CDN geladen
- Font Awesome über CDN eingebunden
- Usability & Design Optimierungen im Userpanel
- Fehlerhandling bezüglich $template_to_use und $template_file verbessert
- Userpanel: Logübersicht überarbeitet
- Userpanel: Zahglreiche Infotexte hinzugefügt

### Game Server

- Neue Game Server Templates: Tekkit, Just Cause 2, sauerbratenremod, shootmania, trackmania, ut2004, ut99, warsow
- .lua Unterstützung für geschütze Configs hinzugefügt
- .lua wird kopiert an stelle von Symlink erstellt.
- Verbesserte Mapgroup Unterstützung
- Verbesserte Workshop Unterstützung
- "Game Rootserver" in Menü "Game Server" verlagert
- game Templates werden standardmäßig nach ihrem shorten sortiert
- Voreingestellte Game Server Addons im Installer
- Spinner in der GS mMasterserver Übersicht hinzugefügt
- Gameroots können nun Resellern zugewiesen werden
- Eingabe von FTP Daten verbessert
- Logdarstellung von Game Server verbessert
- Game Templates können nun genauer definiert werden
- Maxram und OS können bei Gameroots verwaltet werden
- Userpanel: Fastdownload verbessert
- Tabellen Struktur in der Config Edit Übersicht entfernt.
- Infobubble bei den SteamApi Keys
- Userpanel: Game Serverübersicht neu gestaltet
- Quakestat durch GameQ ersetzt
- GameQ um Just Cause 2 Multiplayer erweitert

### Benutzer

- Reseller können sich nicht mehr selber in der User Übersicht bearbeiten
- Funktion User_Permissions verbessert
- CPU last durch password check und migration gesenkt

### Voice Server

- Besseres Error Handling im Bereich Userpanel Voice > Backup
- Connectioncheck beim Anlegen eines TSDNS Masters
- Userpanel: Voiceserver Einstellungen verbessert
- Userpanel: Voiceserver Backup verbessert
- Userpanel: Voiceserver Übersicht verbessert

## Bugfixes

- Reseller Support Tickets Templates fehlend
- Resellers Reseller kann keine Gruppen zu einem User hinzufügen
- Reseller hat keine eigenem Gametemplates
- Reseller eines Resellers kann keine Passwörter ändern
- Direkter Logout Nach Switch zu Reseller
- CFGs werden beim Starten des Protection Modus nicht transferiert
- Footbales und TR beim Restart Kalender fehlend
- TS3 Tokens können nicht erstellt werden
- Benutzer Sortier Funktion
- Voice + Usergroup Rechte werden nicht gespeichert
- Hinzufügen von Dedicated Servern
- Ausgeliehene TS3 Server zu früh gestoppt
- Falscher Redirect nach TS3 DNS hinzufügen
- $_SERVER['REMOTE_ADDR'] in der get_password.php
- &amp&amp; bei der Pagination
- Vertreter Hinzufügen mit bcrypt verwendet falschen SQL
- Restart Planer leitet auf das Dashboard um
- Beim GS Restart wird nicht resynct
- Check fehlt, ob Masterserver existiert
- TS3 Backup Modul
- Template Fehler beim Anlegen eines Game Servers
- Veraltertes Notice Icon beim Login
- Return Nachrichten funktionieren seit 4.11 nicht
- Userpanel: addons
