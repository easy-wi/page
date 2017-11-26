# Easy-Wi Update 5.0

## Important

The control.sh is replaced by a PHP based class. Also Quotas can be used at gameservers. This means you need to alter your/etc/sudoers. Entries for Quotas are optional:

```sh
easywi ALL = NOPASSWD: /usr/sbin/useradd
easywi ALL = NOPASSWD: /usr/sbin/userdel
easywi ALL = NOPASSWD: /usr/sbin/deluser
easywi ALL = NOPASSWD: /usr/sbin/usermod
easywi ALL = NOPASSWD: /usr/sbin/setquota
easywi ALL = NOPASSWD: /usr/sbin/repquota
easywi ALL = (ALL, !root:easywi) NOPASSWD: /home/easywi/temp/*.sh
```

Depending how you named the masteruser `easywi` needs to be replaced.

## Changes

### API

- TSNDS API added
- More speaking access denied error message
- Send operation is returned for debugging
- Complete data set is returned at edit operations
- IP is returned at Game and voice server edit
- Game switch games can be added/removed at the edit operation
- FTP user is returned at game server operations
- Initial password can be set for game servers
- Core count is returned for game servers
- Added list of all installed game types/master apps
- Added list of all master server with optional limit
- Multiple master IDs can be send during all add operations
- Description is returned at master lists
- Added Web space master list
- Added MySQL master list
- Generated user name is returned in case none is send
- Added user list
- New operation clean user's externalID

### CMS

- hreflang support
- index.php is routed to home when seo mode is active
- WYSIWYG editor Summernote for page and news management

### Feeds

- External news in steam feeds are read and added
- Pictures are removed from feeds

### Game Server

- Quota support
- Multiple hard disks are supported
- SteamCMD login can be maintained per template/image
- control.sh replaced by PHP Class
- Configuration previously done at the control.sh replaced by app server configuration
- Protected Linux system user will be only created when the game server has the mode enabled
- SteamCMD updates are executed after each other instead of combined
- Optional option [no_padding] at add ons and additional start commands
- Query port can be defined at the game server template
- New template No More Room in Hell
- New template Project Cars
- FTP server without chroot are supported
- Lending Minecraft, Samp and Teeworlds is supported
- statuscheck.php timeout increased
- Restart done by a cronjob is logged with ip 127.0.0.1
- "@" and "." allowed for FTP user at FastDL

### Miscellaneous

- New admin/user template with 6 different colours
- Large parts of the code re factored
- Creation processes are 1 step only
- SSH ips can be used for ssh connect only to be able to set up a dmz
- Icon and text at the header can be configured at the settings
- Status page for cronjobs and PHP extensions
- Third party CSS, JS and Fonts are shipped with Easy-Wi
- Query results are processed with while instead of foreach loops to reduce ram usage
- Modul concept redone
- CURRENT_TIMESTAMP supported at table repair
- User can deactive info texts
- Char "-" can be used for passwords
- Default externalID is now "empty"
- Job entries for stopping all services are written when a user is deactivated or deleted
- Improved error response at external auth

### MySQL

- externalID can be maintained for databases

### Tickets

- HTML5 validation added to avoid 404 errors

### Voice Server

- externalID can be maintained for TSNDS
- Maximum amount of TSNDS per master can be defined
- Description for Voice Server can be maintained

### Webspace

- Multiple domains can be mapped to a web space
- Optional php.ini configurations can be defined

### Third Party

- Added DataTables
- Added Chosen
- Added moment.js
- Added Daterangepicker
- Updated Bootstrap
- Updated Font Awesome
- Updated HybridAuth

## Bugfixes

- Validator class and multi dimensional arrays
- Installer without error message in case of incorrect MySQL access data
- Only one source of time at lend.php
- External auth is using wring port for SSL
- SSL/TLS support at PHPMailer
- Custom Colums
- Bcrypt support not checked in any case
- Prefix ignored at user adding as resller
- Voice master with external TSDNS master
- Incorrect value for nextfree at lend API
- PHP notice message with stopped voice server
- MySQL overview with incorrect index
- SQL exception at MySQL DB API edit
- TSDNS key login not working
- Http server not starting after edit
- E-Mail template for user add and registration cannot be edited
- DB dump cannot be downloaded