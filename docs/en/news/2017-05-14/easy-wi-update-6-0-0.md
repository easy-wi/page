# Easy-Wi Update 6.0.0

## Remark

The migration script has to be executed on each root server with game servers after the update:
[migrate.sh](https://github.com/easy-wi/server/blob/master/migrate.sh)

## Changes

### General

- Hybrid Auth updated to 2.9.5
- Ubuntu 16.04 support
- added russian language
- Globale search removed
- Admins will be notified in case Easy-Wi installation becomes outdated
- Length for names for public keyfiles globally increased to 255
- Versioning via GitHub instead of easy-wi.com

### CMS

- Download modul can maintain external downloads
- HTTP Only is set in case of https

### Game Server

- ip_port sub folder removed
- Workaround -nobreakpad added at CS:GO template
- GameQ updated to latest dev version
- Server is stopped before reinstall
- Project Cars template updated
- Special character @ can be used for addon folders
- Backup create command will be ignored in case one is running
- Server is stopped before migration is done
- Server description can be maintained
- Fast download instructions added for UnrealEngine
- Steam Server and Game ID can be maintained in parallel

### Voice Server

- Token can be used while adding via API
- Inifile is specified on restart
- Server description can be maintained

### Webspace

- Added PHP-FPM support
- Default redirects added to standard templates

### MySQL

- Added MySQL 5.7 support
- MySQL master description can be maintained

### Installer

- Developer and stable release train configurable

## Bugfixes

- General: Glyphicons used, but not available
- General: Updater from 5.22 to 5.30 error prone if executed multiple times
- General: Variable feedArray undefined in some cases at admin home
- General: Custom modules not properly listed at user menu
- General: To short password leads to failing API
- General: Substitute is not greeted properly
- General: Admin can access users without having the proper permission
- General: SQL error in case imported users are updated and have been imported with md5 password
- General: Redirect after logout on systems without domain not working
- CMS: Summernote editor broken at sites and news
- CMS: News edit and removal of keywords not possible in parallel
- CMS: User activation link
- CMS: Lend servers do not work in case SEO URLs are deactivated
- Game Server: FTP connect at serverlog incorrectly displayed
- Game Server: Securing CVARs in multiple files at once not working
- Game Server: Long INI files are cut off
- Game Server: API FTP password change not reflected to root
- Game Server: Italian translation at Monsta FTP
- Game Server: Typo at game server update mail
- Game Server: Typo at master server menu entry
- Game Server: Shorten with a leading number will crash the API
- Game Server: Upload of empty files at MonstaFTP not possible
- Game Server: Copy of configs at protection mode not working
- Voice Server: Creation via API fails
- Voice Server: SSH Keys at for master do not work
- Voice Server: SSH Keys with password fail for TSDNS master
- Voice Server: Reset of notified at statuscheck failing
- Voice Server: API TSDNS delete does not work
- Voice Server: Masterid at reimport not set
- Voice Server: Typo at voice master outdated mail
- Voice Server: Suhosin check during import will break importer on systems without Suhosin
- Voice Server: Incorrect error message at connection check
- Voice Server: Versions lookup at removed mirror removed
- Webspace: SSH Keys at for master do not work
- Webspace: Usage of fixed urls at vhost template not possible
- API: User list not working with active debig mode
- Installer: Single quote at values for config.php result in syntax error
- Installer: User passwort validation missing
- Installer: Valid password format might be rejected
- Installer: Undefined variable ui