# Easy-Wi Update 4.0

## Changes

### General

- Changed: famfamfam flag icons are used.
- Changed: Remove buttons are highlighted in red.
- Changed: Bootstrap template is now default template
- Added: Danish language (thx @MikkelDK)

### CMS

- Added: Download modul

### Game Server

- Added: games and addons settings can be ex- and imported as/with XML files.
- Changed: Rewrite of ssh2 connect and execute function allowing faster processing.
- Added: Colored highlighting at the overview.

### User

- Added: Changelog regarding userdata
- Added: Users can manage substitutes

### Voice Server

- Added: server vars can be edited at userpanel virtualserver_reserved_slots, virtualserver_needed_identity_security_level, virtualserver_hostmessage_mode, virtualserver_hostbanner_gfx_interval, virtualserver_antiflood_points_tick_reduce, virtualserver_antiflood_points_needed_command_block, virtualserver_antiflood_points_needed_ip_block
- Added: Colored highlighting at the overview.

## Bugfixes

- ESX(i) VM is not properly added/started
- Configlist is not showing addon configs in protection mode
- Receiver and sender flipped at SMTP mode

## Edited template files

- *_header.tpl
- userpanel_voice_md.tpl
- admin_*_list.tpl
- admin_addons_add.tpl
- admin_images_add.tpl
- admin_versioncheck.tpl

## Edited XML language files

- general.xml
- page.xml
- voice.xml