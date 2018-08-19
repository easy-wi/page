# Settings

## Introduction

Each user of the type "Reseller" can make their own settings here. A reseller account will be shown the data regarding imprint and hotline number, which will be set by the admin.

If a "Reseller" creates own "Reseller" accounts, these accounts see his entries.

## General Settings

### Standard Language

The language chosen here is used when logging in and when a user has not yet selected a language and the language of his browser is not available on the panel.

### Template

If more than one template has been installed, it can be activated here.

### Skin

Templates can deliver skins. If one is activated, you can activate the desired skin here.

### Time Zone

If a reseller lives in a different time zone than the web host, he can set the time difference here, so that he does not have to calculate the time difference for every entry with the restart- and backup planner.

### Telephone Number of the Support

In the standard template, the number of the support is shown on the top right, if it is specified here.

### Favicon

### Header Icon

### Header Text

### Header href

### Login Head Text

### Developer Version

## Cronjobs

### Warning

If you do not need a cronjob and want to deactivate the warning that it did not run, you can select "No" here.

### Cronjob IPs

If you call the PHP files from an external server using wget, curl, or similar, you have to whitelist this server.
In the text field you can enter an IP per line.

## User

### Allowed Number of Fails

If a user repeatedly enters the password and/or username incorrectly, the IP address will be blocked for 30 minutes when the limit set here is reached.

### Specify Username / Username

You have the choice to enter usernames yourself, or to use a common user name, to which a unique ID will be appended.

If you select "Yes", then the ID will be appended to the name specified under "Username". User then becomes user2, user3, user4, etc.

## Game Server + Voice Server

### Offline Checks

If the query against a server has failed as often as set here, an attempt is made to restart it.

### Servertag

You can activate the function on game servers to check the server day. If it is active, it checks if the server name contains the server tag specified here.
If this is not the case the user and the admin will be informed and warned.

### Game Server

#### Servertag removed

#### Passwort removed

#### Slots manipulated

#### Images and Game Server are dragged from this server if they do not already exist in the master folder of the gameroot

If you have more than one server, it makes sense to use an image server to centrally manage add-ons and extensions for game servers.

How to set up one can be found in [Image Server Installtion](/en/installation-image-server/).

You can set up a server or user exclusively for this task, or specify an existing installation of a master user.

If a master server is created or updated, a comparison is made to an image server specified here. If you specify more than one, then the one that is in the same subnet as the root server is taken, so that only internal traffic is generated.

Both http and ftp servers can be specified here. For each image server, an extra line must be used.
You have to use the following format:

```sh
http://1.1.2.2
ftp://username:passwort@1.1.3.2
```

### Voice Server

#### Maximum Backups

The maximum number of backups for voice servers. If more are created, the oldest will be deleted automatically.

#### Voice Autobackup

Automatically backup voice servers.

#### Every X Days

The interval in days that automatic backups are created.
