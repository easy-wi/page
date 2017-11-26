# Easy-Wi Update 4.10

## Changes

### General

- News feeds are active per default.
- CMS is activated per default.
- Cronjobs can be executed from remote host in case the IP is whitelisted.
- Link at versionckeck are changed to the new Easy-WI forums location.
- Passwordforms are masked with stars.
- News created at the CMS module are displayed at the dashboard as well.
- Multiple legacy functions removed or optimized.
- Keyfiles can be entered with and without .pub.
- Removal buttons are displayed with fitting icon and in red.
- Modul Management added.

### API

- Passwort hashes are imported as well.

### Game Server

- Root description will be displayed while adding a Game Server. Fallback is the IP.
- While adding or editing a masterserver the connection data will be verified and a connection check done.
- Addons now have a multiselect regarding supported games in case of selecting a game or a whole engine type.
- Minecraft Craft Bukkit startcommand extended.
- l4d, l4d2 and tf2 images are defined with steamCmd installer.
- l4d2 and tf2 are added to the workaround function regarding appIDs for API and updater.
- Added Multi Theft San Andreas image and query.
- Added GTA San Andreas Multiplayer image and query.
- Added Teeworlds image and query.
- Added Minecraft autoupdater.
- Added Minecraft Craft Bukkit autoupdater.
- In case a whole Root Server is lost and replaced all users and server can be recreated with one click.

### MySQL

- Description can be added with a MYSQL database.

### User

- Language variables added regarding users creation and modifcation date.
- Passwords are hashed with PHP 5.5 Hash API or fallback if PHP is older.
- Migration of old hashes once a user logs in.
- Loginname will be shown at Welcome: (...) in case no first and last name is maintained.
- Any hints regarding account existence removed from password reset.

### Voice Server

- While adding or editing a masterserver the connection data will be verified and a connection check done.
- Masterserver can be added to a reseller account which then will be able to use it but cannot see configurations like passwords.

## Bugfixes

- Colours correct at admins Game Server overview.
- Game lendserver are shut down correctly.
- No PHP time out in case the TS3 server bans the webserver during command execution.
- Creation- and modification date correctly setup for initial admin account.
- Outdated icon regarding userswitch removed from logoverview.
- Return after useraction at the ticket module corrected.
- Correct validator used in case of editing own userdata.
- Outdated icons replaced at protectioncheck within the CMS.
- Lendserver overview is displayed correctly at CMS.
- MYSQL module maintains DB users without errors.
- Success message in case of adding a substitute.
- Added missing template admin_voicemasterserver_dl.tpl.
- Corrected reinstall Game Servern at adminpanel.
- Startcommand can now contain the character #.
- Corrected image ALT at protection mode display.
- Enhanced error handling at TS3 class in case no serverinfo has been retrieved.
- Streetnumber can contain a horizontal line.
- Corrected PHP Notice in case of Game Server reinstall.
- Corrected userpanel gamerserver overview regarding FTP passwords.
- FastDL matching working again.
- Usage of $_SERVER removed from login.php.
- Installer definines the default template.