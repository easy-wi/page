# Easy-Wi Update 4.3

## Announcement

The PECL SSH2 extension is no longer needed!

## Changes

### General

- Split Root Server menu in two
- Allow additional login method key + password
- Replace ssh2 pecl module with phpseclib
- Change to red button and trash icon for delete
- Define timezone
- use $dbConnect['debug'] instead of $debug
- Run REPAIR and OPTIMIZE only once a day
- Create FTP class
- Use PHP Mailer for better Mail support

### Game Server

- Add Web FTP
- File templates for Game Server
- Catch Exceptions from GameQ at image.php
- Move GS masterupdate reboot.php -> startupdates.php
- Create functions_gs.php
- Upgrade GameQ to latest version
- Add "select all" to DB repair GS + Addons
- Ensure unique games at gs masterupdate
- Remove color tags from servername
- Enhance output reboot.php/startupdates.php
- Enhance error reporting at screenlog
- Add ESL CS GO addons
- Add tekkit classic
- More debugging output to statuscheck.php
- use binport at teeworlds template
- Add CSS BHOP mappackage
- Add JSON support to config protect
- On Resync/Reinstall preselect template 1
- Add starbound template
- Increase length of gamebinary
- / in front of import path
- Add a gametemplate for reseller if admin does

### Installer

- Predate cronjob timestamps during install
- Display both wget options at install
- Add version check at install

### Root Server

- After image install only PXE remove, no DHCP remove

### User

- Add reseller fix job

### Voice Server

- split content of class_voice.php

## Bugfixes

- API not working due to incorrect validators at vorlage.php
- GS roots reinstall all uses wrong ID
- Protectioncheck form link and subfolders
- Game Server API <installGames> getting ignored
- Registration activation link incorrect if SEO is OFF
- Incorrect display if ticket has been edited
- User cannot reply to tickets in state "In Process"
- Spamfilter set to NO not respected
- Installer fallbacks to non existing language
- Cronjob timestamps for resellers are not updated
- No error handling in case keyfile is missing
- Multiple wrong text displays at installer
- install.php: Undefined index: USER
- Add +1 Slot at check when sourcetv is active
- Error at lending module
- Old SQL on ts3 import regarding usergroup
- Initial password not set during import
- implode(): Invalid arguments userpanel_gserver.php
- Undefined index: active at statuscheck.php
- Remove include for queries.php
- Usernames and TS3 import
- Correct depencies while correct/add default addons