# Easy-Wi Update 5.2

## Changes

### CMS

- Default order of news and date as sort option
### Game Server

- Added universal game server console
- Added Unreal Tournament 3/4 support
- Fetch Ark Survival Evolved Version from arkdedicated.com instead of steam API
- Improved Ark Survival Evolved restart process
- Added Steam Server Token support
- Default imageserver is not hard coded anymore
- Set default start updates at to minute 10
- Added optional parameter at startupdates.php all_root and force_update
- Upgrade to latest GameQ v3 version
- Added additional games to GameQ v3
- Added fallback to GameQ v2
- Added logging at job.php
- Restart all gameserver after master update in any case
- Ensure MC download path is set
- File extension lang is copied
- Better error handling at image import
- Added online mode to MC templates
- Added templates Arma3, Rust, Spigot, Hexxit

### Voice Server

- Flexible configurations possible

### Webspace

- Added version check in Apache Vhost

### General

- New table version and configuration management
- BB code at feed news display added
- Added new skins light skins for all existing colours
- Upgraded UI frameworks to latest versions
- Increased minimum PHP to 5.4
- Display last cron run at system overview
- Deactivate CMS module by default
- Deactivate root module
- Incorrect default open_basedir template
- Incorrect default apache2 reload command

## Bugfixes

- CMS frontend still active when deactivated in backend
- FastDL is showing username instead of domain
- Installer does not work with MySQL package from Oracle
- Corrected list of allowed files at .htaccess
- Align .htaccess with 2.4
- Webmaster: Incorrect redirect to overview in case of error
- % character not within span group in some template files
- Incorrect default MB value at web master
- Wrong URL at installer
- Csgo template outdated
- DataTables not working without because of upper case parameters
- Voice API add method failing with debug on
- Admin GS reinstall: Usage of not existing variable
- Incorrect usage of ID at web master add
- Incorrect array used at ajax app details template
- Incorrect spelling of access
- False positive with outdated voice server version
- Missing queryPassword column at voice server
- Gameserver easy config and special character like newline
- cloud.php cannot be used via external cronjob
- Game Server file copy exclude pattern not applied
- Im Fehler Fall wird "My Voiceserver" erneut voran gestellt
