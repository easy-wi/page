# Easy-Wi Update 5.30

## Remark

This update includes two important security fixes. It is recommended to update as fast as possible.

## Changes

### Game Server

- Added GoTV demo upload support
- Ensure that incorrect RAM settings do not prevent gs add

### Settings

- Added SMTP connection
- New E-Mail template management

### Miscellaneous

- Supressed error return of missing tables at DB repair
- Code preperation for semantic versioning
- Added RSS Feed with Twitter API 1.1
- Automatic redirection to install folder
- Slogan support at login page
- Upgraded HybridAuth to 2.6.0
- Upgraded PHP Mailer to 5.2.14
- Upgraded jQuery to 2.2.3
- Upgraded Summernote to 0.8.1
- Upgraded Chosen to 1.5.1
- Upgraded Font Awesome to 4.6.2

## Bugfixes

- XSS at game server log
- Incomplete TS3 group validation at token create
- Migrate game server using incorrect path
- steamclient.so not found on valve server start up
- Minecraft templates
- Incorrect HTML tag br is added at addon description display
- Missing fastcgi.conf include at Nginx fpm template