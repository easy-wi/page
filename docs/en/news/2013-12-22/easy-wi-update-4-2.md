# Easy-Wi Update 4.2

## Changes

### General

- Added user, substitute, Game Server and Voice Server importer
- Database menu add game and addon repair added
- Rename first menu entry "Dashboard" to "Home"
- CMS and Lendserver active/inactive through module management
- New WEB installer
- Enhanced Header
- Enhanced Easy-WI Settings
- Enhanced Imprint
- Included bootstrap with public CDN
- Include Font Awesome with bootstrap and load from CDN
- Usability & design optimisations at userpanel
- error handling regarding $template_to_use and $template_file
- userpanel: logoverview reworked
- userpanel: multiple infotexts are added

### Game Server

- New Game Server templates: Tekkit, Just Cause 2, sauerbratenremod, shootmania, trackmania, ut2004, ut99, warsow
- added .lua support to protected configs
- .lua files will be copied
- Improved map group support
- Reworked workshop support
- "Game Root Server" moved to "Game Server" menu
- Sort by game images with shorten name by default
- Game Server addons added with installer
- Spinner to GS masterserver overview
- Possible to assign gameroot to a reseller
- Entering FTP improved; Instead of string now multiple fields
- Enhanced Game Server log display
- Extend Game Images
- Add maxram and OS select to gameroots
- userpanel: fastdownload
- Removed tables from config edit
- Infobubble at SteamApi Keys
- userpanel: Game Serveroverview reworked
- Replaced Quakestat with GameQ
- Enhanced GameQ with Just Cause 2 Multiplayer support

### User

- Resellers not allowed to edit themselves at useroverview
- Enhanced function User_Permissions
- Reduced CPU cost of password check and migration

### Voice Server

- Better error handling at Userpanel Voice > Backup
- Check (SSH2) Login TSDNS Master
- userpanel: Voice Server settings improved
- userpanel: Voice Server backup improved
- userpanel: Voice Server overview improved

## Bugfixes

- Reseller support tickets templates missing
- Reseller´s reseller cannot add groups to user
- Reseller cannot own gametemplate
- Reseller of a reseller cannot change password
- Direct logout after reseller login switch
- CFGs are not transferred on protection mode activation
- Add footbales to restart calendar, TR missing
- TS3 Tokens cannot be generated
- User sort function at overview adds additional whitespaces
- voice + usergroup permission not saved
- Adding dedicated servers
- Lended TS3 server with users connected stopped before time is up
- Redirect incorrect after TS3 DNS add
- $_SERVER['REMOTE_ADDR'] should not be used at get_password.php
- &amp&amp; at pagination
- Adding substitute with bcrypt hash with incorrect SQL
- Restart caclendar redirects to dashboard
- On GS restart resync is not done
- No check if masterserver exists
- TS3 Backup Module not working properly
- Template error when adding a Game Server
- old notice icon used at login
- Return messages broken since 4.11
- userpanel: addons