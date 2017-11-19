## Änderungen

### CMS

- Standard sortierung der news geändert und sortieren nach Datum

### Game Server

- Universelle Game Server Konsole hinzugefügt
- Unreal Tournament 3/4 Support hinzugefügt
- Versionsnummer bezüglich Ark Survival Evolved Version wird von arkdedicated.com an Stelle der Steam API bezogen
- Verbesserter Ark Survival Evolved Restart Prozess
- Steam Server Token support hinzugefügt
- Standard Imageserver ist nicht mehr hard coded.
- Standard Start Updates Minute ist nun 10
- Optionale Parameter all_root und force_update zu startupdates.php hinzugefügt
- Auf aktuellste GameQ v3 Version aktualisiert
- Zusätzliche Spiele zu GameQ v3 hinzugefügt
- Fallback auf GameQ v2 erstellt
- Logging in der job.php hinzugefügt
- Game Server werden nach einem Master Update neu gestartet
- Fallbacks für den Minecraft Download Pfad eingeführt
- File Extension lang wird kopiert
- Verbesserte Fehler Behandlung beim Image Import
- Online Modus den MC Templates hinzugefügt
- Templates Arma3, Rust, Spigot, Hexxit hinzugefügt

### Voice Server

- Flexible Konfigurationen möglich

### Webspace

- Apache Vhost Template um Versionsprüfung erweitert

### Allgemeines

- Neues Tabellen Konfigurationsmanagement
- BB Code unterstützung im News Fedd
- Zusätzliche neue Light Skins für alle bereits verfügbaren Farben
- Alle eingesetzten UI frameworks auf aktuellste Version aktualisiert
- Minimale PHP Version ist nun 5.4
- Anzeige des letztmaligen Ausführens der Cronjobs
- CMS standardmäßig deaktiviert
- Root Modul Code auskommentiert

## Bugfixes

- CMS Frontend aktiv, obwohl im Backend deaktiviert
- FastDL zeigt Benutzername an Stelle der Domain
- Installer funktioniert nicht mit dem MySQL Paket von Oracle
- Liste der zugelassenen Dateien in der .htaccess korrigiert
- .htaccess an Apache 2.4 angepasst
- Webmaster: Falscher Redirect zur Übersicht im Falle eines Fehlers
- % Zeichen nicht innerhalb einer span Gruppe bei mehreren Template Dateien
- Falscher standard MB Wert beim Web Master
- Falsche URL beim Installer
- CS:GO Template veraltet
- DataTables funktionieren nicht, wenn Upper Case Character verwendet werden
- Voice API Hinzufügen Methode funktioniert beim aktivierten Debugger nicht
- Admin GS Reinstall: Gebrauch nicht existierender Variable
- Falscher Gebrauch von ID bei Web Master Hinzufügen
- Falscher Gebrauch von array im ajax App Details Template
- Falsche rechtschreibung von access
- False Positive bezüglicher veralteten Voice Server Versionen
- Fehlende queryPassword Spalte bei Voice Servern
- Game Server Easy Config und Special Character, wie Newline
- cloud.php kann nicht mit external Cronjob genutzt werden
- Game Server file copy exclude Pattern nicht angewendet
- On error, "My Voice Server" is prepended on the voice master servers default name
- Falsches open_basedir im Template
- Falscher Default apache2 reload Befehl