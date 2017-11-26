# Easy-Wi Update 4.4

## Changes

### General

- Replaced Wiki with manual links
- Log global usage statistics and display at admin dashboard.
- Easy-wi Facebook page added to headers.
- Additional fallbacks for user_language removed.
- Display only relevant Steam news at user dashboard.
- Display list of available custom modules.
- Substitutes can maintain their own data.
- New PHP folderstructure.
- PNG usage entfernt.
- Social Auth added.

### CMS

- user prefix is NO allows nickname pick at register.
- Display html title depending on the page.

### Game Server

- Allow multiple subfolders for game images.
- Add restart jobs, when steamgame update.
- Moved masterserver ajax out of settings.php
- GameQ updated.
- Add garrysmod template.
- Reduce memory usage with serverlogs.
- Workaround at statuscheck.php for games with different query port.
- Redirect back to restartplaner after edit.
- Workaround for servercolor/branding
- SQL support for EAC.
- Removed hldsupdatetool.

### MySQL

- Hosttable management can be deactivated for users.
- Added reinstall feature.
- Collect and display DB size at MySQL Module.
- Align layout for MySQL to GS at userpanel.

### Root Server

- Enhanced subnet management.
- Reworked Root Server IP system.
- Added Vlan Support.

### User

- Add reseller fix job

### Voice Server

- Add banlist for users to TS3.
- Display slot and traffic usage for TS3 at userpanel.
- Log traffic in addition to slots for TS3 server.

### Webspace

- Webspace/FastDL Modul added.

## Bugfixes

- API: Creating users no password will be saved in the database.
- API: Restore legacy API behaviour.
- CMS: Canurl not set for static pages.
- Game Server: Fix Popup for create NEW FILE WebFTP.
- Game Server: Own Game Server start command.
- Game Server: Minecraft migration does not work.
- Game Server: Game Server Settings Mapgroup selection.
- Game Server: Updates not starting at minute 0.
- Game Server: Restart calendar works for monday only.
- Game Server: Do not export downloadPath with Game Server image.
- Game Server: Protection mode not copying over files from non-protected server.
- Game Server: Online servers with empty server names show up as offline in Webinterface.
- Game Server: Game Server not stopped by job.php on delete.
- General: Workaround for admins without timezone set.
- General: After fresh install mails send without text.
- General: Redirect to URIs with double slashes.
- General: EasyWi CMS links partially incorrect.
- Voice: Missing include while voice server delete.
- Voice: TS3 slots can be edited after reset.