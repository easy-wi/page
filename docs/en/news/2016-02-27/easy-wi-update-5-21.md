# Easy-Wi Update 5.21

## Changes

### CMS

- List of sub pages available at the page template

### Game Server

- Restart after Update can be deactivated
- User can deactivate auto restarts
- JSON can be edited via Web FTP
- RAM is taken into account on master usage
- Live console changed to monospace font
- Passiv FTP is supported

### Voice Server

- Default value for connectIpOnly defined
- Flex slots configuration hidden

### MySQL

- More error details in at MySQL DB CRUD
- More default values at MySQL Master add defined

## Bugfixes

- GS cannot be edited in case root is full
- All GS of root will be restarted in case of any update
- HDD value not saved at GS API
- GS restart not working for some MC cases
- GS cannot be deployed
- Too many files are copied with GS sync/add
- GS backups removed on restart
- Configs listed twice at some templates
- Regex not properly escaped in same config edit cases
- MySQL master password displayed with type text
- MySQL add/mod does not handle SQL external errors
- Incorrect templates at page CRUD
- Page edit does not set variable naviDisplay
- Page keywords not always working
- PHP config not displayed at Web Master
- Maximum voice backups are limited to 9
- Newest TS3 version not detected
- Voice API does not convert JSON config
- Incorrect sucess display at job log
- E-Mail Umlaute und Anordnung
- Web master selection
- Web quota with multiple partitions