# Installer Update 1.3

## Changes

- Additional check if home folder is existing
- Each sudoers configuration is checked individually
- Master user is added to additional group in case of edit
- Hard coded ProFTPd config is now dynamically generated
- ProFTPd whitelist aligned with Easy-Wi templates
- No dialog in case of creating self signed certificates
- Apache module version will be activated if existing
- Journaled quota instead of normal quota
- Improved MySQL process without multiple password prompts
- MySQL can be installed stand alone

## Bugfixes

- MySQL external access configuration incomplete
- LOCAL_IP not set when system language is not English
- SSL configuration is added again on repeated install