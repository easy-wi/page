# Easy-Wi Update 4.11

## Remarks

Unfortunately errors have slipped in. In addition the update revealed that there are still admins with old PHP versions around. Those admins could not login anymore since Easy-Wi has become incompatible.

4.11 is a hotfix release which addresses these problems.

## Changes

- password hash fallback from fallback
- deaktivate register_globals if on

## Bugfixes

- Substitute login failing
- gs backup templates with incorrect variable server_id
- incorrect link at esxi host link
- Minecraft Query not working
- wrong tsdns_settings.ini syntax