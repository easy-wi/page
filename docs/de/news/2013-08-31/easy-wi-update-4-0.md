# Easy-Wi Update 4.0

## Ankündigung

Easy-WI ist mit der Version 4.0 Open Source. Lizenz ist die GNU GPL v3. Die bestehenden Dateien können jederzeit durch quelloffene ersetzt werden. Die GNU GPL v3 lizenzierte Version hat den Funktionsumfang der früheren unbegrenzten gewerblichen Version.

Die bearbeiteten Entwickler Tickets können in unserem Github Repository eingesehen werden.

## Upgrade Anleitung

Version 4.00 ist ein Drop in Replacement. Durch Ioncube Restriktionen kann nicht von 3.70 auf 4.00 im Panel geupgraded werden. Das Gleiche gilt für die control welche von der control.sh ersetzt wird.

Downloade das Komplettpaket in unserem Download Bereich

### Upgrading Web

- Uploade den gesamten Inhalt des web/ Ordners in deine easy-wi Web Installation
- Öffne den Updater http://yourdomain.tld/install/update.php
- Entferne den install/ Ordner vom Webspace

### Upgrading Game Root Server

- Uploade die control.sh in das home/ Verzeichnis des Easy-WI Masterusers; Dies ist der Ort, an dem auch die control platziert ist.
- Ändere das chmod zu 750: chmod 750 control.sh
- Führe visudo aus, um die /etc/sudoers zu editieren und füge folgende Zeile hinzu: deinMasterUser ALL = (ALL, !root:deinMasterUser) NOPASSWD: /home/deinMasterUser/control.sh

## Änderungen

### Generell

- Geändert: famfamfam Flag Icons verwendet.
- Geändert: Entfernen Buttons sind rot.
- Geändert: Bootstrap Template ist nun default
- Hinzugefügt: Dänische Sprache (thx @MikkelDK)

### CMS

- Hinzugefügt: Download Modul

### Game Server

- Hinzugefügt: Spiel Templates und Addon Einstellungen können mit XML Dateien im- und exportiert werden
- Geändert: SSH2 connect und execute Funktionen wurden komplett überarbeitet und erlauben ein schnelleres prozessieren
- Hinzugefügt: Der Serverstatus wird im Admin Menü in der Übersicht farblich dargestellt

### User

- Hinzugefügt: Changelog wenn Userdaten geändert werden
- Hinzugefügt: Benutzer können Vertreter verwalten

### Voice Server

- Hinzugefügt: Im Userpanel können nun folgende Werte geändert werden: virtualserver_reserved_slots, virtualserver_needed_identity_security_level, virtualserver_hostmessage_mode, virtualserver_hostbanner_gfx_interval, virtualserver_antiflood_points_tick_reduce, virtualserver_antiflood_points_needed_command_block, virtualserver_antiflood_points_needed_ip_block
- Hinzugefügt: Der Serverstatus wird im Admin Menü in der Übersicht farblich dargestellt

## Bugfixes

- ESX(i) VM nun korrekt gestartet
- Config Liste enthält nur noch zulässige Configs im Protection Mode
- Empfänger und Sender waren SMTP Modus vertauscht

## Bearbeitete Template Dateien

- *_header.tpl
- userpanel_voice_md.tpl
- admin_*_list.tpl
- admin_addons_add.tpl
- admin_images_add.tpl
- admin_versioncheck.tpl

## Bearbeitete XML Sprachdateien

- general.xml
- page.xml
- voice.xml
