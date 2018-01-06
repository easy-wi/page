# Easy-Wi Update 6.0.4

## Changes

### General

- IPv6 adresses can be logged
- Multiple improvements at the Italian language package

### Game Server

- GameQ Query library updated
- Start/Stop button added at the console in the user area
- Workaround for Debian 9 and screen -L added
- CSV files are copied instead of being linked

## Bugfixes

- Game name not displayed at console output of statuscheck.php
- Game server status time stamp at user overview
- DB remove only of game server outputs shell debug and fails
- Restart of game server with a not existing protected file creates folders recursively
- "Notified count" not reset in case game server is reachable again
- Update success for SteamCMD games no longer detected
- Restart planer not working with latest MySQL on Ubuntu 16.04
- ARK Template
- MTA:SA Template
- Page list not working with latest MySQL on Ubuntu 16.04
- CMS cannot be edited in some cases
- In case a TS3 master belongs to a reseller the instances are not checked properly by status check
- Initial TS3 password not saved to DB
- suhosin check at TS3 import
- Incorrect headline at TSDNS admin overview
- Adding groups with active debugger not working
- Multiple undefined variable notices (with active debugger)
- Incorrect icon used from Font Awesome in case of Hybridauth and Twitch
- Security issue in case Reseller switches to a user account
- SQL syntax at game and voice server API in combination with external ID
- Login Loop (first login might fail)
- "Please allow redirection settings" error in case of logout on some systems
- Adding a ticket category with latest MySQL on Ubuntu 16.04 fails
- Redirect at default Apache2 vhost template